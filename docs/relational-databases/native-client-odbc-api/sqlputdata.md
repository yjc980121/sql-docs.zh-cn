---
title: SQLPutData | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 89e694b18dc27a739a7e1f4d1e0950ef08a01570
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73785744"
---
# <a name="sqlputdata"></a>SQLPutData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  当使用 SQLPutData 发送超过65535个字节的数据（对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本 4.21 a）或 400 KB 的数据（对于 SQL Server 版本6.0 和更高版本 **）（对于**版本和更高**版本 SQL_LONGVARCHAR）** 时 SQL_LONGVARBINARY SQL_WLONGVARCHAR，以下限制将适用：  
  
-   引用的参数可以是 INSERT 语句中的*insert_value* 。  
  
-   引用的参数可以是 UPDATE 语句的 SET 子句中的*表达式*。  
  
 当使用版本6.5 或更早版本时，取消将向运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的服务器提供块数据的 SQLPutData 调用序列会导致列值的部分更新。 调用 SQLCancel 时引用的**text**、 **ntext**或**image**列被设置为中间占位符值。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序不支持连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 版和更低版本。  
  
## <a name="diagnostics"></a>诊断  
 对于 SQLPutData，有一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 特定的 SQLSTATE：  
  
|SQLSTATE|Error|描述|  
|--------------|-----------|-----------------|  
|22026|字符串数据，长度不匹配|如果应用程序已指定要发送的数据的长度（以字节为单位），例如，使用 SQL_LEN_DATA_AT_EXEC （*n*），其中*n*大于0，则应用程序通过 SQLPutData 指定的字节总数必须与指定的长度匹配。|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a>SQLPutData 和表值参数  
 使用带有表值参数的可变行绑定时，应用程序将使用 SQLPutData。 *StrLen_Or_Ind*参数指示它已准备好供驱动程序为表值参数数据的下一行或多行收集数据，或者没有更多的可用行：  
  
-   大于 0 的值指示可以使用下一组行值。  
  
-   0 值指示已没有更多的行要发送。  
  
-   任何小于 0 的值则会出错，导致记录一个诊断记录，该记录包含 SQLState HY090 和消息“字符串或缓冲区长度无效”。  
  
 *DataPtr*参数将被忽略，但必须设置为非 NULL 值。 有关详细信息，请参阅有关[表值参数和列值的绑定和数据传输](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)中的变量 TVP 行绑定部分。  
  
 如果*StrLen_Or_Ind*包含除 SQL_DEFAULT_PARAM 以外的任何值或介于0和 SQL_PARAMSET_SIZE 之间的数字（即，SQLBindParameter 的*ColumnSize*参数），则是错误的。 此错误导致 SQLPutData 返回 SQL_ERROR：SQLSTATE=HY090，“字符串或缓冲区长度无效”。  
  
 有关表值参数的详细信息，请参阅[表值参数&#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a>SQLPutData 对增强的日期和时间功能的支持  
 日期/时间类型的参数值按[从 C 转换到 SQL](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)中所述的方式进行转换。  
  
 有关详细信息，请参阅[日期和时间&#40;改进&#41;ODBC](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)。  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a>SQLPutData 对大型 CLR UDT 的支持  
 **SQLPutData**支持大型 CLR 用户定义类型（udt）。 有关详细信息，请参阅[大型 CLR 用户定义类型&#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)。  
  
## <a name="see-also"></a>另请参阅  
 [SQLPutData 函数](https://go.microsoft.com/fwlink/?LinkId=59365)   
 [ODBC API 实现细节](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
