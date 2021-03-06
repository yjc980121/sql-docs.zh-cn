---
title: 创建、更改和删除触发器
ms.custom: seo-dt-2019
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- triggers [SMO]
ms.assetid: 8ddbe23b-6e31-4f8e-8a70-17bd5072413e
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f4e6b81723b986974003d376b84dc7b53a96fb29
ms.sourcegitcommit: 15fe0bbba963d011472cfbbc06d954d9dbf2d655
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/14/2019
ms.locfileid: "74094509"
---
# <a name="creating-altering-and-removing-triggers"></a>创建、更改和删除触发器
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]
  在 SMO 中，触发器由 <xref:Microsoft.SqlServer.Management.Smo.Trigger> 对象表示。 在激发的触发器由触发器对象的 <xref:Microsoft.SqlServer.Management.Smo.Trigger.TextBody%2A> 属性设置时运行的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 代码。 使用 <xref:Microsoft.SqlServer.Management.Smo.Trigger> 对象的其他属性（如 <xref:Microsoft.SqlServer.Management.Smo.Trigger.Update%2A> 属性）可以设置触发器的类型。 这是一个布尔属性，该属性指定是否由对父表上的记录的**更新**触发触发器。  
  
 <xref:Microsoft.SqlServer.Management.Smo.Trigger> 对象表示传统的数据操作语言 (DML) 触发器。 在 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 和更改版本中，也同样支持数据定义语言 (DDL) 触发器。 DDL 触发器由 <xref:Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger> 对象和 <xref:Microsoft.SqlServer.Management.Smo.ServerDdlTrigger> 对象表示。  
  
## <a name="example"></a>示例  
若要使用所提供的任何代码示例，您必须选择创建应用程序所需的编程环境、编程模板和编程语言。 有关详细信息，请参阅[在 Visual Studio&#35; .Net 中创建 Visual C SMO 项目](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。  
 
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-basic"></a>在 Visual Basic 中创建、更改和删除触发器  
 此代码示例演示如何在 `Sales` 数据库中名为 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 的现有表上创建并插入更新触发器。 当更新表或插入新记录时触发器会发送提醒消息。  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim mysrv As Server
mysrv = New Server
'Reference the AdventureWorks2012 2008R2 database.
Dim mydb As Database
mydb = mysrv.Databases("AdventureWorks2012")
'Declare a Table object variable and reference the Customer table.
Dim mytab As Table
mytab = mydb.Tables("Customer", "Sales")
'Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.
Dim tr As Trigger
tr = New Trigger(mytab, "Sales")
'Set TextMode property to False, then set other properties to define the trigger.
tr.TextMode = False
tr.Insert = True
tr.Update = True
tr.InsertOrder = Agent.ActivationOrder.First
Dim stmt As String
stmt = " RAISERROR('Notify Customer Relations',16,10) "
tr.TextBody = stmt
tr.ImplementationType = ImplementationType.TransactSql
'Create the trigger on the instance of SQL Server.
tr.Create()
'Remove the trigger.
tr.Drop()
``` 
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-c"></a>在 Visual C# 中创建、更改和删除触发器  
 此代码示例演示如何在 `Sales` 数据库中名为 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 的现有表上创建并插入更新触发器。 当更新表或插入新记录时触发器会发送提醒消息。  
  
```csharp  
{  
            //Connect to the local, default instance of SQL Server.   
            Server mysrv;  
            mysrv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database mydb;  
            mydb = mysrv.Databases["AdventureWorks2012"];  
            //Declare a Table object variable and reference the Customer table.   
            Table mytab;  
            mytab = mydb.Tables["Customer", "Sales"];  
            //Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.   
            Trigger tr;  
            tr = new Trigger(mytab, "Sales");  
            //Set TextMode property to False, then set other properties to define the trigger.   
            tr.TextMode = false;  
            tr.Insert = true;  
            tr.Update = true;  
            tr.InsertOrder = ActivationOrder.First;  
            string stmt;  
            stmt = " RAISERROR('Notify Customer Relations',16,10) ";  
            tr.TextBody = stmt;  
            tr.ImplementationType = ImplementationType.TransactSql;  
            //Create the trigger on the instance of SQL Server.   
            tr.Create();  
            //Remove the trigger.   
            tr.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-trigger-in-powershell"></a>在 PowerShell 中创建、更改和删除触发器  
 此代码示例演示如何在 `Sales` 数据库中名为 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 的现有表上创建并插入更新触发器。 当更新表或插入新记录时触发器会发送提醒消息。  
  
```powershell  
# Set the path context to the local, default instance of SQL Server and to the  
#database tables in Adventureworks2012  
CD \sql\localhost\default\databases\AdventureWorks2012\Tables\  
  
#Get reference to the trigger's target table  
$mytab = get-item Sales.Customer  
  
# Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.  
$tr  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Trigger `  
-argumentlist $mytab, "Sales"  
  
# Set TextMode property to False, then set other properties to define the trigger.   
$tr.TextMode = $false  
$tr.Insert = $true  
$tr.Update = $true  
$tr.InsertOrder = [Microsoft.SqlServer.Management.SMO.Agent.ActivationOrder]::First  
$tr.TextBody = " RAISERROR('Notify Customer Relations',16,10) "  
$tr.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Create the trigger on the instance of SQL Server.   
$tr.Create()  
  
#Remove the trigger.   
$tr.Drop()  
```  
  
  
