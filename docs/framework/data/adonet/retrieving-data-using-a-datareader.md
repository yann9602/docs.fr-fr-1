---
title: "Extraction de donn&#233;es &#224; l&#39;aide d&#39;un DataReader | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Extraction de donn&#233;es &#224; l&#39;aide d&#39;un DataReader
L'extraction de données à l'aide d'un **DataReader** implique la création d'une instance de l'objet **Command**, puis la création d'un **DataReader** en appelant **Command.ExecuteReader** pour extraire des lignes d'une source de données.  Voici un exemple d'utilisation d'un **DataReader** où `reader` représente un DataReader valide et `command` représente un objet Command valide.  
  
```  
reader = command.ExecuteReader();  
```  
  
 Vous utilisez la méthode **Read** de l'objet **DataReader** pour obtenir une ligne à partir des résultats de la requête.  Vous pouvez accéder à chaque colonne de la ligne retournée en passant le nom ou la référence ordinale de la colonne au **DataReader**.  Cependant, pour une meilleure performance, le **DataReader** fournit une série de méthodes qui vous permettent d'accéder aux valeurs de colonne dans leurs types de données natifs \(**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, etc.\).  Pour obtenir une liste de méthodes d'accesseur typées pour les **DataReaders** spécifiques au fournisseur de données, voir les objets <xref:System.Data.OleDb.OleDbDataReader> et <xref:System.Data.SqlClient.SqlDataReader>.  L'utilisation des méthodes d'accesseur typées, lorsque le type de données sous\-jacent est connu, réduit le volume de conversion de types requis lors de l'extraction de la valeur de colonne.  
  
> [!NOTE]
>  La version Windows Server 2003 du .NET Framework inclut une propriété supplémentaire pour le **DataReader**, **HasRows**, qui vous permet de déterminer si le **DataReader** a retourné des résultats avant d'y lire.  
  
 L'exemple de code suivant itère au sein d'un objet **DataReader** et retourne deux colonnes à partir de chaque ligne.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
 Le **DataReader** fournit un flux de données non mis en tampon qui permet à la logique procédurale de traiter efficacement les résultats provenant d'une source de données de façon séquentielle.  Le **DataReader** se révèle être un bon choix lors de l'extraction de grandes quantités de données car celles\-ci ne sont pas mises en cache dans la mémoire.  
  
## Fermeture du DataReader  
 Vous devez toujours appeler la méthode **Close** lorsque vous avez fini d'utiliser l'objet **DataReader**.  
  
 Si **Command** contient des paramètres de sortie ou des valeurs de retour, ils ne seront pas disponibles avant la fermeture du **DataReader**.  
  
 Notez que pendant l'ouverture d'un **DataReader**, **Connection** est utilisé en mode exclusif par ce **DataReader**.  Vous ne pouvez pas exécuter de commandes pour **Connection**, y compris la création d'un autre **DataReader**, jusqu'à la fermeture du **DataReader** d'origine.  
  
> [!NOTE]
>  N'appelez pas **Close** ou **Dispose** sur un objet **Connection**, **DataReader** ou tout autre objet managé dans la méthode **Finalize** de votre classe.  Dans un finaliseur, libérez seulement les ressources non managées que votre classe possède directement.  Si votre classe ne possède pas de ressources non managées, n'incluez pas la méthode **Finalize** dans votre définition de classe.  Pour plus d'informations, consultez [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).  
  
## Extraction de plusieurs jeux de résultats à l'aide de NextResult  
 Si des jeux de résultats multiples sont retournés, le **DataReader** fournit la méthode **NextResult** pour itérer sur les jeux de résultats dans l'ordre.  L'exemple suivant montre l'objet <xref:System.Data.SqlClient.SqlDataReader> traitant les résultats de deux instructions SELECT utilisant la méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## Obtention d'informations de schéma à partir du DataReader  
 Lorsqu'un **DataReader** est ouvert, vous pouvez extraire des informations de schéma concernant le jeu de résultats actuel à l'aide de la méthode **GetSchemaTable**.  **GetSchemaTable** retourne un objet <xref:System.Data.DataTable> rempli de lignes et de colonnes qui contiennent les informations de schéma pour le jeu de résultats actuel.  Le  **DataTable** contient une ligne pour chaque colonne du jeu de résultats.  Chaque colonne de la ligne de table de schéma mappe à une propriété de la colonne retournée dans le jeu de résultats, où **ColumnName** est le nom de la propriété et la valeur de la colonne est la valeur de la propriété.  L'exemple de code suivant écrit les informations de schéma pour **DataReader**.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## Utilisation de chapitres OLE DB  
 Les jeux de lignes hiérarchiques ou chapitres \(**DBTYPE\_HCHAPTER** de type OLE DB, **adChapter** de type ADO\) peuvent être extraits à l'aide de l'objet <xref:System.Data.OleDb.OleDbDataReader>.  Lorsqu'une requête comprenant un chapitre est retournée comme **DataReader**, le chapitre est retourné comme colonne dans ce **DataReader** et exposé comme objet **DataReader**.  
  
 Le **DataSet** ADO.NET peut aussi être utilisé pour représenter des jeux de lignes hiérarchiques à l'aide de relations parent\-enfant entre les tables.  Pour plus d'informations, consultez [Objets DataSet, DataTable et DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
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
  
## Retour de résultats avec des REF CURSOR Oracle  
 Le fournisseur de données .NET Framework pour Oracle prend en charge l'utilisation des REF CURSOR Oracle pour retourner le résultat d'une requête.  Un REF CURSOR Oracle est retourné en tant qu'objet <xref:System.Data.OracleClient.OracleDataReader>.  
  
 Vous pouvez extraire un objet **OracleDataReader** qui représente un REF CURSOR Oracle à l'aide de la méthode <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> et également spécifier un objet <xref:System.Data.OracleClient.OracleCommand> qui retourne un ou plusieurs REF CURSOR Oracle en tant que **SelectCommand** d'un objet <xref:System.Data.OracleClient.OracleDataAdapter> utilisé pour remplir un objet <xref:System.Data.DataSet>.  
  
 Pour accéder à un REF CURSOR retourné par une source de données Oracle, créez un **OracleCommand** pour votre requête et ajoutez un paramètre de sortie qui référence le REF CURSOR à la collection **Parameters** de votre **OracleCommand**.  Le nom du paramètre doit correspondre à celui du paramètre REF CURSOR de votre requête.  Définissez **OracleType.Cursor** comme type de paramètre.  La méthode **ExecuteReader** de votre **OracleCommand** retourne un **OracleDataReader** pour REF CURSOR.  
  
 Si votre **OracleCommand** retourne plusieurs REF CURSOR, ajoutez plusieurs paramètres de sortie.  Vous pouvez accéder aux différents REF CURSOR en appelant la méthode **OracleCommand.ExecuteReader**.  L'appel à la méthode **ExecuteReader** retourne un **OracleDataReader** qui référence le premier REF CURSOR.  Vous pouvez ensuite appeler la méthode **OracleDataReader.NextResult** pour accéder aux REF CURSOR suivants.  Bien que les paramètres de votre collection **OracleCommand.Parameters** coïncident par leur nom avec les paramètres de sortie du REF CURSOR, le **OracleDataReader** y accède selon l'ordre de leur ajout à la collection **Parameters**.  
  
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
  
 Le code suivant crée un **OracleCommand** qui retourne les REF CURSOR d'un précédent package Oracle en ajoutant deux paramètres de type **OracleType.Cursor** à la collection **Parameters**.  
  
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
  
 Le code suivant retourne les résultats de la précédente commande à l'aide des méthodes **Read** et **NextResult** de **OracleDataReader**.  Les paramètres REF CURSOR sont retournés dans l'ordre.  
  
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
  
 L'exemple suivant utilise la commande précédente pour remplir un **DataSet** avec les résultats du package Oracle.  
  
> [!NOTE]
>  Pour éviter une **OverflowException**, nous vous recommandons également d'opérer toute conversion du type Oracle NUMBER en un type .NET Framework valide avant de stocker la valeur dans un **DataRow**.  Vous pouvez utiliser l'événement **FillError** pour déterminer si une exception **OverflowException** s'est produite.  Pour plus d'informations sur l'événement **FillError**, voir [Gestion des événements DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
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
  
## Voir aussi  
 [Working with DataReaders](http://msdn.microsoft.com/fr-fr/126a966a-d08d-4d22-a19f-f432908b2b54)   
 [DataAdapters et DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [Commandes et paramètres](../../../../docs/framework/data/adonet/commands-and-parameters.md)   
 [Récupération d'informations de schéma de base de données](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)