---
title: "Récupération de données à l'aide d'un DataReader"
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
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0b66ca2fbcc760598b771b4c02a46acc3c9c1d4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-data-using-a-datareader"></a>Récupération de données à l'aide d'un DataReader
La récupération de données à l’aide un **DataReader** implique la création d’une instance de la **commande** objet, puis en créant un **DataReader** en appelant  **Command.ExecuteReader** pour extraire des lignes à partir d’une source de données. L’exemple suivant montre comment utiliser un **DataReader** où `reader` représente un DataReader valide et `command` représente un objet Command valide.  
  
```  
reader = command.ExecuteReader();  
```  
  
 Vous utilisez la **en lecture** méthode de la **DataReader** objet pour obtenir une ligne à partir des résultats de la requête. Vous pouvez accéder à chaque colonne de la ligne retournée en passant le nom ou la référence ordinale de la colonne à la **DataReader**. Toutefois, pour de meilleures performances, le **DataReader** fournit une série de méthodes qui vous permettent d’accéder aux valeurs de colonne dans leurs types de données natifs (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, et ainsi de suite). Pour obtenir la liste des méthodes d’accesseur typées pour les données spécifiques au fournisseur **DataReaders**, consultez <xref:System.Data.OleDb.OleDbDataReader> et <xref:System.Data.SqlClient.SqlDataReader>. L’utilisation des méthodes d’accesseur typées, lorsque le type de données sous-jacent est connu, réduit le volume de conversion de types requis lors de l’extraction de la valeur de colonne.  
  
> [!NOTE]
>  La version de Windows Server 2003 du .NET Framework inclut une propriété supplémentaire pour le **DataReader**, **HasRows**, ce qui vous permet de déterminer si le **DataReader**a retourné des résultats avant la lecture à partir de celui-ci.  
  
 L’exemple de code suivant itère un **DataReader** objet et retourne deux colonnes à partir de chaque ligne.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
 Le **DataReader** fournit un flux non mis en tampon de données qui permet à la logique procédurale de traiter efficacement les résultats à partir d’une source de données de manière séquentielle. Le **DataReader** est un bon choix lors de la récupération de grandes quantités de données, car les données ne sont pas mis en cache en mémoire.  
  
## <a name="closing-the-datareader"></a>Fermeture du DataReader  
 Vous devez toujours appeler la **fermer** méthode lorsque vous avez fini d’utiliser le **DataReader** objet.  
  
 Si votre **commande** sortie contient des paramètres ou valeurs de retour, ils ne seront pas disponibles tant que le **DataReader** est fermé.  
  
 Notez que pendant un **DataReader** est ouvert, le **connexion** est utilisé exclusivement par qui **DataReader**. Vous ne pouvez pas exécuter de commandes pour le **connexion**, y compris la création d’un autre **DataReader**, jusqu'à ce que l’original **DataReader** est fermé.  
  
> [!NOTE]
>  N’appelez pas **fermer** ou **Dispose** sur un **connexion**, un **DataReader**, ou tout autre objet managé dans le **Finalize**  méthode de votre classe. Dans un finaliseur, libérez seulement les ressources non managées que votre classe possède directement. Si votre classe ne possède pas les ressources non managées, n’incluez pas une **Finalize** méthode dans votre définition de classe. Pour plus d’informations, consultez [le Garbage Collection](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>Extraction de plusieurs jeux de résultats à l'aide de NextResult  
 Si plusieurs jeux de résultats est retournés, le **DataReader** fournit le **NextResult** définit de méthode pour itérer au sein du résultat dans l’ordre. L'exemple suivant montre l'objet <xref:System.Data.SqlClient.SqlDataReader> traitant les résultats de deux instructions SELECT utilisant la méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>Obtention d'informations de schéma à partir du DataReader  
 Pendant un **DataReader** est ouvert, vous pouvez extraire les informations de schéma sur le résultat actuel à l’aide de la **GetSchemaTable** (méthode). **GetSchemaTable** retourne un <xref:System.Data.DataTable> objet rempli avec des lignes et colonnes qui contiennent des informations de schéma pour le jeu de résultats actuel. Le **DataTable** contient une ligne pour chaque colonne du jeu de résultats. Chaque colonne de la ligne de table de schéma mappe à une propriété de la colonne retournée dans le jeu de résultats, où le **ColumnName** est le nom de la propriété et la valeur de la colonne est la valeur de la propriété. L’exemple de code suivant écrit les informations de schéma **DataReader**.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>Utilisation de chapitres OLE DB  
 Ensembles de lignes hiérarchiques ou chapitres (type OLE DB **DBTYPE_HCHAPTER**, type ADO **adChapter**) peuvent être récupérés à l’aide de la <xref:System.Data.OleDb.OleDbDataReader>. Lorsqu’une requête comprenant un chapitre est retournée comme un **DataReader**, le chapitre est retourné comme colonne dans ce **DataReader** et est exposé comme un **DataReader** objet.  
  
 ADO.NET **DataSet** peut également être utilisé pour représenter des jeux de lignes hiérarchiques à l’aide de relations parent-enfant entre les tables. Pour plus d’informations, consultez [DataSets, DataTables et DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 L'exemple de code suivant utilise le fournisseur MSDataShape pour générer une colonne chapitre de commandes pour chaque client d'une liste de clients.  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")  
  
Dim custCMD As OleDbCommand = New OleDbCommand( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
connection.Open()  
  
Dim custReader As OleDbDataReader = custCMD.ExecuteReader()  
Dim orderReader As OleDbDataReader  
  
Do While custReader.Read()  
  Console.WriteLine("Orders for " & custReader.GetString(1))   
  ' custReader.GetString(1) = CompanyName  
  
  orderReader = custReader.GetValue(2)  
  ' custReader.GetValue(2) = Orders chapter as DataReader  
  
  Do While orderReader.Read()  
    Console.WriteLine(vbTab & orderReader.GetInt32(1))  
    ' orderReader.GetInt32(1) = OrderID  
  Loop  
  orderReader.Close()  
Loop  
' Make sure to always close readers and connections.  
custReader.Close()  
End Using  
```  
  
```csharp  
Using (OleDbConnection connection = new OleDbConnection(  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"));  
{  
OleDbCommand custCMD = new OleDbCommand(  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
connection.Open();  
  
OleDbDataReader custReader = custCMD.ExecuteReader();  
OleDbDataReader orderReader;  
  
while (custReader.Read())  
{  
  Console.WriteLine("Orders for " + custReader.GetString(1));   
  // custReader.GetString(1) = CompanyName  
  
  orderReader = (OleDbDataReader)custReader.GetValue(2);        
  // custReader.GetValue(2) = Orders chapter as DataReader  
  
  while (orderReader.Read())  
    Console.WriteLine("\t" + orderReader.GetInt32(1));          
    // orderReader.GetInt32(1) = OrderID  
  orderReader.Close();  
}  
// Make sure to always close readers and connections.  
custReader.Close();  
}  
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Retour de résultats avec des REF CURSOR Oracle  
 Le fournisseur de données .NET Framework pour Oracle prend en charge l'utilisation des REF CURSOR Oracle pour retourner le résultat d'une requête. Un REF CURSOR Oracle est retourné en tant qu'objet <xref:System.Data.OracleClient.OracleDataReader>.  
  
 Vous pouvez récupérer un **OracleDataReader** objet qui représente un REF CURSOR Oracle à l’aide de la <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> (méthode) et vous pouvez également spécifier un <xref:System.Data.OracleClient.OracleCommand> qui retourne un ou plusieurs REF CURSOR Oracle en tant que le  **SelectCommand** pour un <xref:System.Data.OracleClient.OracleDataAdapter> utilisé pour remplir un <xref:System.Data.DataSet>.  
  
 Pour accéder à un REF CURSOR retourné à partir d’une source de données Oracle, créez un **OracleCommand** pour votre requête et ajoutez un paramètre de sortie qui référence le REF CURSOR à la **paramètres** collection de votre  **OracleCommand**. Le nom du paramètre doit correspondre à celui du paramètre REF CURSOR de votre requête. Définir le type du paramètre à **OracleType.Cursor**. Le **ExecuteReader** méthode de votre **OracleCommand** retournera un **OracleDataReader** pour REF CURSOR.  
  
 Si votre **OracleCommand** retourne plusieurs REF CURSOR, ajoutez plusieurs paramètres de sortie. Vous pouvez accéder aux différents REF CURSOR en appelant le **OracleCommand.ExecuteReader** (méthode). L’appel à **ExecuteReader** retourne un **OracleDataReader** qui référence le premier REF CURSOR. Vous pouvez ensuite appeler la **OracleDataReader.NextResult** méthode pour accéder aux REF CURSOR suivants. Bien que les paramètres de votre **OracleCommand.Parameters** collection le REF CURSOR paramètres de sortie par son nom, le **OracleDataReader** y accède selon l’ordre qu’ils ont été ajoutés à la  **Paramètres** collection.  
  
 Considérez, par exemple, le package et le corps de package Oracle suivants.  
  
```  
CREATE OR REPLACE PACKAGE CURSPKG AS   
  TYPE T_CURSOR IS REF CURSOR;   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR);   
END CURSPKG;  
  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR)   
  IS   
  BEGIN   
    OPEN EMPCURSOR FOR SELECT * FROM DEMO.EMPLOYEE;   
    OPEN DEPTCURSOR FOR SELECT * FROM DEMO.DEPARTMENT;   
  END OPEN_TWO_CURSORS;   
END CURSPKG;   
```  
  
 Le code suivant crée un **OracleCommand** qui retourne les REF CURSOR d’un précédent package Oracle en ajoutant deux paramètres de type **OracleType.Cursor** à le **paramètres** collection.  
  
```vb  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
```  
  
```csharp  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
```  
  
 Le code suivant retourne les résultats de la commande précédente à l’aide du **en lecture** et **NextResult** méthodes de la **OracleDataReader**. Les paramètres REF CURSOR sont retournés dans l'ordre.  
  
```vb  
oraConn.Open()  
  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.CommandType = CommandType.StoredProcedure  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
  
Dim reader As OracleDataReader = cursCmd.ExecuteReader()  
  
Console.WriteLine(vbCrLf & "Emp ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2))  
Loop  
  
reader.NextResult()  
  
Console.WriteLine(vbCrLf & "Dept ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}", reader.GetOracleNumber(0), reader.GetString(1))  
Loop  
' Make sure to always close readers and connections.  
reader.Close()  
oraConn.Close()  
```  
  
```csharp  
oraConn.Open();  
  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.CommandType = CommandType.StoredProcedure;  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
  
OracleDataReader reader = cursCmd.ExecuteReader();  
  
Console.WriteLine("\nEmp ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2));  
  
reader.NextResult();  
  
Console.WriteLine("\nDept ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}", reader.GetOracleNumber(0), reader.GetString(1));  
// Make sure to always close readers and connections.  
reader.Close();  
oraConn.Close();  
```  
  
 L’exemple suivant utilise la commande précédente pour remplir un **DataSet** avec les résultats du package Oracle.  
  
> [!NOTE]
>  Pour éviter un **OverflowException**, nous vous recommandons d’également gérer toute conversion à partir du type Oracle NUMBER en un type .NET Framework valide avant de stocker la valeur dans un **DataRow**. Vous pouvez utiliser la **FillError** événement pour déterminer si une **OverflowException** s’est produite. Pour plus d’informations sur la **FillError** événements, consultez [gestion des événements DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
```vb  
Dim ds As DataSet = New DataSet()  
  
Dim adapter As OracleDataAdapter = New OracleDataAdapter(cursCmd)  
adapter.TableMappings.Add("Table", "Employees")  
adapter.TableMappings.Add("Table1", "Departments")  
  
adapter.Fill(ds)  
```  
  
```csharp  
DataSet ds = new DataSet();  
  
OracleDataAdapter adapter = new OracleDataAdapter(cursCmd);  
adapter.TableMappings.Add("Table", "Employees");  
adapter.TableMappings.Add("Table1", "Departments");  
  
adapter.Fill(ds);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de DataReaders](http://msdn.microsoft.com/en-us/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [DataAdapters et DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Commandes et paramètres](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [La récupération des informations de schéma de base de données](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
