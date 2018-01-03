---
title: "Configuration des paramètres et des types de données des paramètres"
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
ms.assetid: 537d8a2c-d40b-4000-83eb-bc1fcc93f707
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0f5aed56ba4958d44e0628f55115308751afae55
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-parameters-and-parameter-data-types"></a>Configuration des paramètres et des types de données des paramètres
Les objets de commande utilisent des paramètres pour passer des valeurs à des instructions SQL ou à des procédures stockées, en fournissant la vérification et la validation des types. Contrairement au texte de la commande, l'entrée de paramètre est traitée comme une valeur littérale et non pas comme du code exécutable. Cela vous permet de vous protéger des attaques « par injection de code SQL », dans lesquelles un attaquant insère une commande qui compromet la sécurité sur le serveur dans une instruction SQL.  
  
 Les commandes paramétrées améliorent également les performances d'exécution des requêtes car elles permettent au serveur de base de données de faire correspondre la commande entrante avec un plan de requête mis en cache approprié. Pour plus d’informations, consultez [Mise en mémoire cache et réutilisation du plan d’exécution](http://go.microsoft.com/fwlink/?LinkId=120424) et [Réutilisation des paramètres et des plans d’exécution](http://go.microsoft.com/fwlink/?LinkId=120423) dans la documentation en ligne de SQL Server. Outre les avantages relatifs à la sécurité et aux performances, les commandes paramétrées fournissent une méthode pratique d'organisation des valeurs passées à une source de données.  
  
 Un objet <xref:System.Data.Common.DbParameter> peut être créé à l'aide de son constructeur ou en l'ajoutant à la propriété <xref:System.Data.Common.DbCommand.DbParameterCollection%2A> en appelant la méthode `Add` de la collection <xref:System.Data.Common.DbParameterCollection> . La méthode `Add` prendra comme entrée des arguments de constructeur ou un objet Parameter existant, selon le fournisseur de données.  
  
## <a name="supplying-the-parameterdirection-property"></a>Fourniture de la propriété ParameterDirection  
 Lorsque vous ajoutez des paramètres, vous devez fournir une propriété <xref:System.Data.ParameterDirection> pour les paramètres autres que les paramètres d'entrée. Le tableau ci-dessous indique les valeurs `ParameterDirection` que vous pouvez utiliser avec l'énumération <xref:System.Data.ParameterDirection> .  
  
|Nom de membre|Description|  
|-----------------|-----------------|  
|<xref:System.Data.ParameterDirection.Input>|Le paramètre est un paramètre d'entrée. Il s'agit de la valeur par défaut.|  
|<xref:System.Data.ParameterDirection.InputOutput>|Le paramètre peut être à la fois un paramètre d'entrée et de sortie.|  
|<xref:System.Data.ParameterDirection.Output>|Le paramètre est un paramètre de sortie.|  
|<xref:System.Data.ParameterDirection.ReturnValue>|Le paramètre représente une valeur de retour d'une opération telle qu'une procédure stockée, une fonction intégrée ou une fonction définie par l'utilisateur.|  
  
## <a name="working-with-parameter-placeholders"></a>Utilisation d'espaces réservés de paramètres  
 La syntaxe des espaces réservés des paramètres dépend de la source de données. Les fournisseurs de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] gèrent différemment la dénomination et la spécification des paramètres et des espaces réservés de paramètres. Cette syntaxe est personnalisée en fonction d'une source de données spécifique, comme le décrit le tableau ci-dessous.  
  
|Fournisseur de données|Syntaxe d'attribution de noms aux paramètres|  
|-------------------|-----------------------------|  
|<xref:System.Data.SqlClient>|Utilise des paramètres nommés au format `@`*nom_paramètre*.|  
|<xref:System.Data.OleDb>|Utilise des marqueurs de paramètres positionnels indiqués par un point d'interrogation (`?`).|  
|<xref:System.Data.Odbc>|Utilise des marqueurs de paramètres positionnels indiqués par un point d'interrogation (`?`).|  
|<xref:System.Data.OracleClient>|Utilise des paramètres nommés au format `:`*nom_paramètre* (ou *nom_paramètre*).|  
  
## <a name="specifying-parameter-data-types"></a>Spécification des types de données de paramètre  
 Le type de données d'un paramètre est spécifique au fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] . Si vous spécifiez le type, la valeur de `Parameter` est convertie en type de fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] avant d'être passée à la source de données. Vous pouvez également spécifier le type d'un `Parameter` de façon générique en affectant à la propriété `DbType` de l'objet `Parameter` un <xref:System.Data.DbType>particulier.  
  
 Le type de fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] d'un objet `Parameter` est déduit à partir du type [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] du `Value` de l'objet `Parameter` ou à partir du `DbType` de l'objet `Parameter` . Le tableau suivant indique le type `Parameter` déduit en fonction de l'objet passé comme valeur `Parameter` ou du `DbType`spécifié.  
  
|Type .NET Framework|DbType|SqlDbType|OleDbType|OdbcType|OracleType|  
|-------------------------|------------|---------------|---------------|--------------|----------------|  
|<xref:System.Boolean>|Boolean|Bit|Booléen|Bit|Byte|  
|<xref:System.Byte>|Byte|TinyInt|UnsignedTinyInt|TinyInt|Byte|  
|byte[]|Binaire|VarBinary`.` cette conversion implicite échouera si le tableau d’octets est supérieur à la taille maximale de VarBinary, soit 8 000 octets. Pour les tableaux d’octets supérieurs à 8 000 octets, définissez explicitement la <xref:System.Data.SqlDbType>.|VarBinary|Binaire|Raw|  
|<xref:System.Char>|``|La déduction de <xref:System.Data.SqlDbType> à partir de char n'est pas prise en charge.|Char|Char|Byte|  
|<xref:System.DateTime>|DateTime|DateTime|DBTimeStamp|DateTime|DateTime|  
|<xref:System.DateTimeOffset>|DateTimeOffset|DateTimeOffset dans SQL Server 2008. La déduction de <xref:System.Data.SqlDbType> à partir de DateTimeOffset n'est pas prise en charge dans les versions de SQL Server antérieures à SQL Server 2008.|||DateTime|  
|<xref:System.Decimal>|Decimal|Decimal|Decimal|Numérique|Nombre|  
|<xref:System.Double>|Double|Float|Double|Double|Double|  
|<xref:System.Single>|Single|Real|Single|Real|Float|  
|<xref:System.Guid>|Guid|UniqueIdentifier|Guid|UniqueIdentifier|Raw|  
|<xref:System.Int16 >|Int16|SmallInt|SmallInt|SmallInt|Int16|  
|<xref:System.Int32>|Int32|Int|Int|Int|Int32|  
|<xref:System.Int64>|Int64|BigInt|BigInt|BigInt|Nombre|  
|<xref:System.Object>|Objet|Variante|Variante|La déduction d'OdbcType à partir d'Object n'est pas prise en charge.|Blob|  
|<xref:System.String>|Chaîne|NVarChar. Cette conversion implicite échouera si la chaîne est supérieure à la taille maximale de NVarChar, soit 4 000 caractères. Pour les chaînes supérieures à 4 000 caractères, définissez explicitement <xref:System.Data.SqlDbType>.|VarWChar|NVarChar|NVarChar|  
|<xref:System.TimeSpan>|réflexion|Time dans SQL Server 2008. La déduction de <xref:System.Data.SqlDbType> à partir de TimeSpan n'est pas prise en charge dans les versions de SQL Server antérieures à SQL Server 2008.|DBTime|réflexion|DateTime|  
|<xref:System.UInt16>|UInt16|La déduction de <xref:System.Data.SqlDbType> à partir de UInt16 n'est pas prise en charge.|UnsignedSmallInt|Int|UInt16|  
|<xref:System.UInt32>|UInt32|La déduction de <xref:System.Data.SqlDbType> à partir de UInt32 n'est pas prise en charge.|UnsignedInt|BigInt|UInt32|  
|<xref:System.UInt64>|UInt64|La déduction de <xref:System.Data.SqlDbType> à partir de UInt64 n'est pas prise en charge.|UnsignedBigInt|Numérique|Nombre|  
||AnsiString|VarChar|VarChar|VarChar|VarChar|  
||AnsiStringFixedLength|Char|Char|Char|Char|  
|``|Devise|Money|Devise|La déduction d' `OdbcType` à partir de `Currency` n'est pas prise en charge.|Nombre|  
|``|Date|Date dans SQL Server 2008. La déduction de <xref:System.Data.SqlDbType> à partir de Date n'est pas prise en charge dans les versions de SQL Server antérieures à SQL Server 2008.|DBDate|Date|DateTime|  
|``|SByte|La déduction de <xref:System.Data.SqlDbType> à partir de SByte n'est pas prise en charge.|TinyInt|La déduction de `OdbcType` à partir de SByte n'est pas prise en charge.|SByte|  
||StringFixedLength|NChar|WChar|NChar|NChar|  
||réflexion|Time dans SQL Server 2008. La déduction de <xref:System.Data.SqlDbType> à partir de Time n'est pas prise en charge dans les versions de SQL Server antérieures à SQL Server 2008.|DBTime|réflexion|DateTime|  
||VarNumeric|La déduction de <xref:System.Data.SqlDbType> à partir de VarNumeric n'est pas prise en charge.|VarNumeric|La déduction de `OdbcType` à partir de VarNumeric n'est pas prise en charge.|Nombre|  
|type défini par l'utilisateur (objet avec <xref:Microsoft.SqlServer.Server.SqlUserDefinedAggregateAttribute>)|Objet ou chaîne, selon le fournisseur (SqlClient retourne toujours un objet, ODBC retourne toujours une chaîne et le fournisseur de données managées OleDb l'un ou l'autre)|SqlDbType.Udt si <xref:Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute> est présent, sinon Variant|OleDbType.VarWChar (si la valeur est Null), sinon OleDbType.Variant.|OdbcType.NVarChar|non pris en charge|  
  
> [!NOTE]
>  Les conversions du type decimal vers d'autres types sont des conversions restrictives qui arrondissent la valeur décimale à la valeur entière la plus proche de zéro. Si le résultat de la conversion ne peut pas être représenté dans le type de destination, un <xref:System.OverflowException> est levé.  
  
> [!NOTE]
>  Lorsque vous envoyez une valeur de paramètre Null au serveur, vous devez spécifier <xref:System.DBNull>, et non `null` (`Nothing` dans [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]). Dans le système, la valeur null désigne un objet vide qui ne possède pas de valeur. <xref:System.DBNull> est utilisé pour représenter des valeurs null. Pour plus d’informations sur les valeurs Null de base de données, consultez [Handling Null Values](../../../../docs/framework/data/adonet/sql/handling-null-values.md).  
  
## <a name="deriving-parameter-information"></a>Dérivation des informations sur les paramètres  
 Les paramètres peuvent aussi être dérivés d'une procédure stockée à l'aide de la classe `DbCommandBuilder` . Les classes `SqlCommandBuilder` et `OleDbCommandBuilder` fournissent une méthode statique, `DeriveParameters`, qui remplit automatiquement la collection de paramètres d'un objet Command qui utilise les informations sur les paramètres provenant d'une procédure stockée. Notez que `DeriveParameters` remplace toutes les informations existantes sur les paramètres pour la commande.  
  
> [!NOTE]
>  La dérivation des informations de paramètre entraîne une baisse des performances car elle requiert un aller-retour supplémentaire vers la source de données pour extraire les informations. Si les informations sur les paramètres sont connues au moment du design, vous pouvez améliorer la performance de votre application en définissant les paramètres de manière explicite.  
  
 Pour plus d’informations, consultez [génération de commandes avec CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).  
  
## <a name="using-parameters-with-a-sqlcommand-and-a-stored-procedure"></a>Utilisation des paramètres avec un objet SqlCommand ou une procédure stockée  
 Les procédures stockées offrent de nombreux avantages dans les applications pilotées par des données. En utilisant les procédures stockées, les opérations de base de données peuvent être encapsulées dans une commande unique, optimisées pour de meilleures performances et améliorées grâce à une sécurité supplémentaire. Bien qu'une procédure stockée puisse être appelée en passant son nom suivi des arguments de paramètre comme instruction SQL, l'utilisation de la collection <xref:System.Data.Common.DbCommand.Parameters%2A> de l'objet [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.Common.DbCommand> vous permet de définir plus explicitement les paramètres de procédure stockée et d'accéder aux paramètres de sortie et aux valeurs de retour.  
  
> [!NOTE]
>  Les instructions paramétrées sont exécutées sur le serveur à l'aide de `sp_executesql,` , ce qui permet la réutilisation des plans de requête. Les curseurs ou variables locaux dans le lot `sp_executesql` ne sont pas visibles pour le lot qui appelle `sp_executesql`. Les modifications dans le contexte de la base de données durent uniquement jusqu'à la fin de l'instruction `sp_executesql` . Pour plus d'informations, voir la documentation en ligne de SQL Server.  
  
 Lorsque vous utilisez des paramètres avec un objet <xref:System.Data.SqlClient.SqlCommand> pour exécuter une procédure stockée SQL Server, les noms des paramètres ajoutés à la collection <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> doivent correspondre à ceux des marqueurs de paramètres dans la procédure stockée. Le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour SQL Server ne prend pas en charge l'espace réservé de point d'interrogation (?) pour le passage des paramètres à une instruction SQL ou une procédure stockée. Il traite les paramètres de la procédure stockée comme des paramètres nommés et recherche les marqueurs de paramètres correspondants. Par exemple, la procédure stockée `CustOrderHist` est définie à l'aide d'un paramètre nommé `@CustomerID`. Lorsque votre code exécute la procédure stockée, il doit également utiliser un paramètre nommé `@CustomerID`.  
  
```  
CREATE PROCEDURE dbo.CustOrderHist @CustomerID varchar(5)  
```  
  
### <a name="example"></a>Exemple  
 Cet exemple montre comment appeler une procédure stockée SQL Server dans l'exemple de base de données `Northwind` . Le nom de la procédure stockée est `dbo.SalesByCategory` et il possède un paramètre d'entrée nommé `@CategoryName` avec un type de données `nvarchar(15)`. Le code crée un nouveau <xref:System.Data.SqlClient.SqlConnection> à l'intérieur d'un bloc using pour que la connexion soit libérée une fois la procédure terminée. Les objets <xref:System.Data.SqlClient.SqlCommand> et <xref:System.Data.SqlClient.SqlParameter> sont créés et leurs propriétés sont définies. Un <xref:System.Data.SqlClient.SqlDataReader> exécute `SqlCommand` et retourne le jeu de résultats provenant de la procédure stockée, en affichant la sortie dans la fenêtre de console.  
  
> [!NOTE]
>  Au lieu de créer les objets `SqlCommand` et `SqlParameter` puis de définir les propriétés dans des instructions distinctes, vous pouvez choisir d'utiliser l'un des constructeurs surchargés pour définir plusieurs propriétés dans une instruction unique.  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
## <a name="using-parameters-with-an-oledbcommand-or-odbccommand"></a>Utilisation des paramètres avec OleDbCommand ou OdbcCommand  
 Lorsque vous utilisez des paramètres avec un objet <xref:System.Data.OleDb.OleDbCommand> ou <xref:System.Data.Odbc.OdbcCommand>, l'ordre des paramètres ajoutés à la collection `Parameters` doit correspondre à celui des paramètres définis dans votre procédure stockée. Les fournisseurs de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour OLE DB et [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour ODBC traitent les paramètres d'une procédure stockée comme des espaces réservés et appliquent des valeurs de paramètre par ordre. En outre, les paramètres des valeurs de retour doivent être les premiers paramètres ajoutés à la collection `Parameters` .  
  
 Les fournisseurs de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour OLE DB et [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour ODBC ne prennent pas en charge les paramètres nommés pour le passage des paramètres à une instruction SQL ou une procédure stockée. Dans ce cas, vous devez utiliser l'espace réservé de point d'interrogation (?), comme dans l'exemple suivant.  
  
```  
SELECT * FROM Customers WHERE CustomerID = ?  
```  
  
 En conséquence, l'ordre dans lequel les objets `Parameter` sont ajoutés à la collection `Parameters` doit directement correspondre à la position de l'espace réservé ? pour le paramètre.  
  
### <a name="oledb-example"></a>Exemple OleDb  
  
```vb  
Dim command As OleDbCommand = New OleDbCommand( _  
  "SampleProc", connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As OleDbParameter = command.Parameters.Add( _  
  "RETURN_VALUE", OleDbType.Integer)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@InputParm", OleDbType.VarChar, 12)  
parameter.Value = "Sample Value"  
  
parameter = command.Parameters.Add( _  
  "@OutputParm", OleDbType.VarChar, 28)  
parameter.Direction = ParameterDirection.Output  
```  
  
```csharp  
OleDbCommand command = new OleDbCommand("SampleProc", connection);  
command.CommandType = CommandType.StoredProcedure;  
  
OleDbParameter parameter = command.Parameters.Add(  
  "RETURN_VALUE", OleDbType.Integer);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add(  
  "@InputParm", OleDbType.VarChar, 12);  
parameter.Value = "Sample Value";  
  
parameter = command.Parameters.Add(  
  "@OutputParm", OleDbType.VarChar, 28);  
parameter.Direction = ParameterDirection.Output;  
```  
  
## <a name="odbc-example"></a>Exemple Odbc  
  
```vb  
Dim command As OdbcCommand = New OdbcCommand( _  
  "{ ? = CALL SampleProc(?, ?) }", connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As OdbcParameter = command.Parameters.Add("RETURN_VALUE", OdbcType.Int)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@InputParm", OdbcType.VarChar, 12)  
parameter.Value = "Sample Value"  
  
parameter = command.Parameters.Add( _  
  "@OutputParm", OdbcType.VarChar, 28)  
parameter.Direction = ParameterDirection.Output  
```  
  
```csharp  
OdbcCommand command = new OdbcCommand( _  
  "{ ? = CALL SampleProc(?, ?) }", connection);  
command.CommandType = CommandType.StoredProcedure;  
  
OdbcParameter parameter = command.Parameters.Add( _  
  "RETURN_VALUE", OdbcType.Int);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add( _  
  "@InputParm", OdbcType.VarChar, 12);  
parameter.Value = "Sample Value";  
  
parameter = command.Parameters.Add( _  
  "@OutputParm", OdbcType.VarChar, 28);  
parameter.Direction = ParameterDirection.Output;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes et paramètres](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Paramètres DataAdapter](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [Mappages de types de données dans ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
