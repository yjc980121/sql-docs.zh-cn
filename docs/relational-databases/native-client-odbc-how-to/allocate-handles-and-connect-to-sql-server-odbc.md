---
title: 分配句柄并连接到 SQL Server （ODBC） |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- handles [ODBC]
- handles [ODBC], connection
- handles [ODBC], about handles
ms.assetid: 6172cd52-9c9a-467d-992f-def07f3f3bb1
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ce294636c4d01a143b640126832bc6cca31ece14
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73782066"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a>分配句柄并连接到 SQL Server (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a>分配句柄并连接到 SQL Server  
  
1.  包含 ODBC 头文件 Sql.h、Sqlext.h、Sqltypes.h。  
  
2.  包含特定于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驱动程序的头文件 Odbcss.h。  
  
3.  使用 SQL_HANDLE_ENV 的**HandleType**调用[SQLALLOCHANDLE](https://go.microsoft.com/fwlink/?LinkId=58396)以初始化 ODBC 并分配环境句柄。  
  
4.  调用[SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md)并将**属性**设置为 SQL_ATTR_ODBC_VERSION，并将**将 valueptr**设置为 SQL_OV_ODBC3，以指示应用程序将使用 ODBC 1.x 格式函数调用。  
  
5.  也可以调用[SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md)来设置其他环境选项，或调用[SQLGetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=58403)来获取环境选项。  
  
6.  使用 SQL_HANDLE_DBC 的**HandleType**调用[SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) ，以分配连接句柄。  
  
7.  也可以调用[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)来设置连接选项，或调用[SQLGetConnectAttr](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md)来获取连接选项。  
  
8.  调用 SQLConnect，使用现有数据源连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
     或  
  
     调用[SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md)以使用连接字符串连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
     最小的完整 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接字符串采用以下两种格式之一：  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     如果连接字符串不完整， **SQLDriverConnect**可能会提示输入所需的信息。 这是由为*DriverCompletion*参数指定的值控制的。  
  
     \- 或 -  
  
     多次调用[SQLBrowseConnect](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)以生成连接字符串并连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
9. 也可以调用[SQLGetInfo](../../relational-databases/native-client-odbc-api/sqlgetinfo.md)来获取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据源的驱动程序属性和行为。  
  
10. 分配并使用语句。  
  
11. 调用 SQLDisconnect 断开与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的连接，并使连接句柄可用于新连接。  
  
12. 使用 SQL_HANDLE_DBC 的**HandleType**调用[SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) ，以释放连接句柄。  
  
13. 使用 SQL_HANDLE_ENV 的**HandleType**调用**SQLFreeHandle** ，以释放环境句柄。  
  
> [!IMPORTANT]  
>  请尽可能使用 Windows 身份验证。 如果 Windows 身份验证不可用，请在运行时提示用户输入其凭据。 不要将凭据存储在一个文件中。 如果必须保存凭据，应当用 [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532)（Win32 加密 API）加密它们。  
  
## <a name="example"></a>示例  
 此示例演示对**SQLDriverConnect**的调用，以连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例，而无需使用现有的 ODBC 数据源。 通过将不完整的连接字符串传递给**SQLDriverConnect**，它会使 ODBC 驱动程序提示用户输入缺少的信息。  
  
```  
#define MAXBUFLEN   255  
  
SQLHENV      henv = SQL_NULL_HENV;  
SQLHDBC      hdbc1 = SQL_NULL_HDBC;  
SQLHSTMT      hstmt1 = SQL_NULL_HSTMT;  
  
SQLCHAR      ConnStrIn[MAXBUFLEN] =  
         "DRIVER={SQL Server Native Client 10.0};SERVER=MyServer";  
  
SQLCHAR      ConnStrOut[MAXBUFLEN];  
SQLSMALLINT   cbConnStrOut = 0;  
  
// Make connection without data source. Ask that driver   
// prompt if insufficient information. Driver returns  
// SQL_ERROR and application prompts user  
// for missing information. Window handle not needed for  
// SQL_DRIVER_NOPROMPT.  
retcode = SQLDriverConnect(hdbc1,      // Connection handle  
                  NULL,         // Window handle  
                  ConnStrIn,      // Input connect string  
                  SQL_NTS,         // Null-terminated string  
                  ConnStrOut,      // Address of output buffer  
                  MAXBUFLEN,      // Size of output buffer  
                  &cbConnStrOut,   // Address of output length  
                  SQL_DRIVER_PROMPT);  
```  
  
  
