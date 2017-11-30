---
title: "Spécification de valeurs XML comme paramètres"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2c4d08b8-fc29-4614-97fa-29c8ff7ca5b3
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4d48cc329644873be268606409c154ffe832cd91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-xml-values-as-parameters"></a><span data-ttu-id="d20f5-102">Spécification de valeurs XML comme paramètres</span><span class="sxs-lookup"><span data-stu-id="d20f5-102">Specifying XML Values as Parameters</span></span>
<span data-ttu-id="d20f5-103">Si une requête requiert un paramètre dont la valeur est une chaîne XML, les développeurs peuvent fournir cette valeur à l’aide d’une instance de la **SqlXml** type de données.</span><span class="sxs-lookup"><span data-stu-id="d20f5-103">If a query requires a parameter whose value is an XML string, developers can supply that value using an instance of the **SqlXml** data type.</span></span> <span data-ttu-id="d20f5-104">Il n'y a réellement pas d'astuces ; les colonnes XML dans [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] acceptent les valeurs de paramètre exactement de la même manière que d'autres types de données.</span><span class="sxs-lookup"><span data-stu-id="d20f5-104">There really are no tricks; XML columns in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] accept parameter values in exactly the same way as other data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d20f5-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="d20f5-105">Example</span></span>  
 <span data-ttu-id="d20f5-106">L’application console suivante crée une nouvelle table dans le **AdventureWorks** base de données.</span><span class="sxs-lookup"><span data-stu-id="d20f5-106">The following console application creates a new table in the **AdventureWorks** database.</span></span> <span data-ttu-id="d20f5-107">La nouvelle table inclut une colonne nommée **SalesID** et une colonne XML nommée **SalesInfo**.</span><span class="sxs-lookup"><span data-stu-id="d20f5-107">The new table includes a column named **SalesID** and an XML column named **SalesInfo**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d20f5-108">Le **AdventureWorks** base de données exemple n’est pas installé par défaut lorsque vous installez [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d20f5-108">The **AdventureWorks** sample database is not installed by default when you install [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d20f5-109">Vous pouvez l'installer en exécutant l'Installation de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d20f5-109">You can install it by running SQL Server Setup.</span></span>  
  
 <span data-ttu-id="d20f5-110">L'exemple prépare un objet <xref:System.Data.SqlClient.SqlCommand> à insérer une ligne dans la nouvelle table.</span><span class="sxs-lookup"><span data-stu-id="d20f5-110">The example prepares a <xref:System.Data.SqlClient.SqlCommand> object to insert a row in the new table.</span></span> <span data-ttu-id="d20f5-111">Un fichier enregistré fournit les données XML nécessaires pour le **SalesInfo** colonne.</span><span class="sxs-lookup"><span data-stu-id="d20f5-111">A saved file provides the XML data needed for the **SalesInfo** column.</span></span>  
  
 <span data-ttu-id="d20f5-112">Pour créer le fichier nécessaire pour l’exécution de l’exemple, créez un nouveau fichier texte dans le même dossier que votre projet.</span><span class="sxs-lookup"><span data-stu-id="d20f5-112">To create the file needed for the example to run, create a new text file in the same folder as your project.</span></span> <span data-ttu-id="d20f5-113">Nommez le fichier MyTestStoreData.xml.</span><span class="sxs-lookup"><span data-stu-id="d20f5-113">Name the file MyTestStoreData.xml.</span></span> <span data-ttu-id="d20f5-114">Ouvrez le fichier dans Bloc-notes, puis copiez et collez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="d20f5-114">Open the file in Notepad and copy and paste the following text:</span></span>  
  
```xml  
<StoreSurvey xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>300000</AnnualSales>  
  <AnnualRevenue>30000</AnnualRevenue>  
  <BankName>International Bank</BankName>  
  <BusinessType>BM</BusinessType>  
  <YearOpened>1970</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>7000</SquareFeet>  
  <Brands>3</Brands>  
  <Internet>T1</Internet>  
  <NumberEmployees>2</NumberEmployees>  
</StoreSurvey>  
```  
  
```vb  
Imports System  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Xml  
  
Module Module1  
    Sub Main()  
  
        Using connection As SqlConnection = New SqlConnection(GetConnectionString())  
        connection.Open()  
  
        ' Create a sample table (dropping first if it already  
        ' exists.)  
        Dim commandNewTable As String = _  
         "IF EXISTS (SELECT * FROM dbo.sysobjects " & _  
         "WHERE id = object_id(N'[dbo].[XmlDataTypeSample]') " & _  
         "AND OBJECTPROPERTY(id, N'IsUserTable') = 1) " & _  
         "DROP TABLE [dbo].[XmlDataTypeSample];" & _  
         "CREATE TABLE [dbo].[XmlDataTypeSample](" & _  
         "[SalesID] [int] IDENTITY(1,1) NOT NULL, " & _  
         "[SalesInfo] [xml])"  
  
        Dim commandAdd As New _  
         SqlCommand(commandNewTable, connection)  
        commandAdd.ExecuteNonQuery()  
  
        Dim commandText As String = _  
         "INSERT INTO [dbo].[XmlDataTypeSample] " & _  
           "([SalesInfo] ) " & _  
           "VALUES(@xmlParameter )"  
  
        Dim command As New SqlCommand(commandText, connection)  
  
        ' Read the saved XML document as a   
        ' SqlXml-data typed variable.  
        Dim newXml As SqlXml = _  
         New SqlXml(New XmlTextReader("MyTestStoreData.xml"))  
  
        ' Supply the SqlXml value for the value of the parameter.  
        command.Parameters.AddWithValue("@xmlParameter", newXml)  
  
        Dim result As Integer = command.ExecuteNonQuery()  
        Console.WriteLine(result & " row was added.")  
        Console.WriteLine("Press Enter to continue.")  
        Console.ReadLine()  
    End Using  
End Sub  
  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,              
        ' you can retrieve it from a configuration file.   
        Return "Data Source=(local);Integrated Security=SSPI;" & _  
          "Initial Catalog=AdventureWorks"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Xml;  
using System.Data.SqlTypes;  
  
class Class1  
{  
    static void Main()  
    {  
        using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
       {  
        connection.Open();  
        //  Create a sample table (dropping first if it already  
        //  exists.)  
  
        string commandNewTable =   
            "IF EXISTS (SELECT * FROM dbo.sysobjects " +   
            "WHERE id = " +  
                  "object_id(N'[dbo].[XmlDataTypeSample]') " +   
            "AND OBJECTPROPERTY(id, N'IsUserTable') = 1) " +   
            "DROP TABLE [dbo].[XmlDataTypeSample];" +   
            "CREATE TABLE [dbo].[XmlDataTypeSample](" +   
            "[SalesID] [int] IDENTITY(1,1) NOT NULL, " +   
            "[SalesInfo] [xml])";  
        SqlCommand commandAdd =   
                   new SqlCommand(commandNewTable, connection);  
        commandAdd.ExecuteNonQuery();  
        string commandText =   
            "INSERT INTO [dbo].[XmlDataTypeSample] " +   
            "([SalesInfo] ) " +   
            "VALUES(@xmlParameter )";  
        SqlCommand command =   
                  new SqlCommand(commandText, connection);  
  
        //  Read the saved XML document as a   
        //  SqlXml-data typed variable.  
        SqlXml newXml =   
            new SqlXml(new XmlTextReader("MyTestStoreData.xml"));  
  
        //  Supply the SqlXml value for the value of the parameter.  
        command.Parameters.AddWithValue("@xmlParameter", newXml);  
  
        int result = command.ExecuteNonQuery();  
        Console.WriteLine(result + " row was added.");  
        Console.WriteLine("Press Enter to continue.");  
        Console.ReadLine();  
    }  
  }  
  
    private static string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,              
        // you can retrieve it from a configuration file.   
        return "Data Source=(local);Integrated Security=true;" +  
        "Initial Catalog=AdventureWorks; ";  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d20f5-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d20f5-115">See Also</span></span>  
 <xref:System.Data.SqlTypes.SqlXml>  
 [<span data-ttu-id="d20f5-116">Données XML dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="d20f5-116">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 [<span data-ttu-id="d20f5-117">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="d20f5-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
