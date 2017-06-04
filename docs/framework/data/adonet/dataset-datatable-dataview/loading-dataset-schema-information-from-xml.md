---
title: "Chargement des informations de sch&#233;ma d&#39;un DataSet &#224; partir de XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Chargement des informations de sch&#233;ma d&#39;un DataSet &#224; partir de XML
Le schéma d'un objet <xref:System.Data.DataSet> \(ses tables, colonnes, relations et contraintes\) peut être défini par programme, créé par la méthode **Fill** ou **FillSchema** d'un objet <xref:System.Data.Common.DataAdapter> ou chargé à partir d'un document XML.  Pour charger les informations de schéma d'un **DataSet** à partir d'un document XML, vous pouvez utiliser la méthode **ReadXmlSchema** ou **InferXmlSchema** du **DataSet**.  **ReadXmlSchema** vous permet de charger ou de déduire les informations de schéma du **DataSet** à partir du document contenant le schéma en langage XSD \(XML Schema Definition\) ou d'un document XML avec le schéma XML inline.  **InferXmlSchema** vous permet de déduire le schéma à partir du document XML tout en ignorant certains espaces de noms XML que vous spécifiez.  
  
> [!NOTE]
>  Le classement des tables dans un **DataSet** peut ne pas être préservé lorsque vous utilisez des services Web ou la sérialisation XML pour transférer un **DataSet** qui a été créé en mémoire à l'aide de constructions XSD \(telles que des relations imbriquées\).  Par conséquent, le destinataire du **DataSet** ne doit pas dépendre du classement des tables dans ce cas.  Toutefois, le classement des tables est toujours préservé si le schéma du **DataSet** transféré a été lu à partir des fichiers XSD, au lieu d'être créé en mémoire.  
  
## ReadXmlSchema  
 Pour charger le schéma d'un **DataSet** à partir d'un document XML sans charger les données, vous pouvez utiliser la méthode **ReadXmlSchema** du **DataSet**.  **ReadXmlSchema** crée le schéma du **DataSet** à l'aide du schéma en langage XSD \(XML Schema Definition\).  
  
 La méthode **ReadXmlSchema** accepte un argument unique représentant le nom d'un fichier, un flux ou un **XmlReader** contenant le document XML à charger.  Le document XML peut contenir uniquement le schéma ou contenir le schéma inline avec des éléments XML contenant des données.  Pour plus d'informations sur l'écriture d'un schéma inline sous forme de schéma XML, voir [Dérivation de la structure relationnelle d'un DataSet à partir d'un schéma XML \(XSD\)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
 Si le document XML passé à **ReadXmlSchema** ne contient aucune information de schéma inséré, **ReadXmlSchema** déduira le schéma des éléments figurant dans le document XML.  Si le **DataSet** contient déjà un schéma, le schéma en cours sera étendu par l'ajout de nouvelles tables si elles n'existent pas encore.  De nouvelles colonnes ne seront pas ajoutées aux tables existantes.  Si une colonne ajoutée existe déjà dans le **DataSet**, mais que son type est incompatible avec la colonne trouvée dans le XML, une exception est levée.  Pour plus d'informations sur la façon dont **ReadXmlSchema** déduit un schéma à partir d'un document XML, voir [Inférence de la structure relationnelle d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).  
  
 Bien que **ReadXmlSchema** charge ou déduit uniquement le schéma d'un **DataSet**, la méthode **ReadXml** du **DataSet** charge ou déduit le schéma et les données contenues dans le document XML.  Pour plus d'informations, consultez [Chargement d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).  
  
 Les exemples de code suivants montrent comment charger le schéma d'un **DataSet** à partir d'un document ou d'un flux XML.  Le premier exemple illustre le cas d'un nom de fichier de schéma XML passé à la méthode **ReadXmlSchema**.  Le second exemple utilise un **System.IO.StreamReader**.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As System.IO.StreamReader = New System.IO.StreamReader ("schema.xsd");  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema(xmlStream)  
xmlStream.Close()  
```  
  
```csharp  
System.IO.StreamReader xmlStream = new System.IO.StreamReader("schema.xsd");  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema(xmlStream);  
xmlStream.Close();  
```  
  
## InferXmlSchema  
 Vous pouvez également faire en sorte que le **DataSet** déduise son schéma à partir d'un document XML en utilisant la méthode **InferXmlSchema** du **DataSet**.  **InferXmlSchema** fonctionne de la même manière que **ReadXml** avec un **XmlReadMode** ayant pour valeur **InferSchema** \(charge les données et déduit le schéma\) et **ReadXmlSchema** si le document lu ne contient pas de schéma inline.  Toutefois, **InferXmlSchema** offre en plus la possibilité de spécifier les espaces de noms XML qui doivent être ignorés lorsque le schéma est déduit.  **InferXmlSchema** prend deux arguments requis : l'emplacement du document XML, spécifié par un nom de fichier, un flux ou un **XmlReader** ; un tableau de chaînes spécifiant les espaces de noms XML qui doivent être ignorés au cours de l'opération.  
  
 Examinons, par exemple, le code XML suivant :  
  
```  
<NewDataSet xmlns:od="urn:schemas-microsoft-com:officedata">  
<Categories>  
  <CategoryID od:adotype="3">1</CategoryID>   
  <CategoryName od:maxLength="15" od:adotype="130">Beverages</CategoryName>   
  <Description od:adotype="203">Soft drinks and teas</Description>   
</Categories>  
<Products>  
  <ProductID od:adotype="20">1</ProductID>   
  <ReorderLevel od:adotype="3">10</ReorderLevel>   
  <Discontinued od:adotype="11">0</Discontinued>   
</Products>  
</NewDataSet>  
```  
  
 En raison des attributs spécifiés pour les éléments dans le document XML précédent, les méthodes **ReadXmlSchema** et **ReadXml** avec une valeur de **XmlReadMode** **InferSchema** créeraient des tables pour chaque élément du document : **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel** et **Discontinued**.  \(Pour plus d'informations, consultez [Inférence de la structure relationnelle d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).\) Toutefois, une structure plus appropriée voudrait dans un premier temps que seules les tables **Categories** et **Products** soient créées et, dans un deuxième temps, que soient créées les colonnes **CategoryID**, **CategoryName** et **Description** pour la table **Categories** et les colonnes **ProductID**, **ReorderLevel** et **Discontinued** pour la table **Products**.  Pour vous assurer que le schéma déduit ignore les attributs spécifiés dans les éléments XML, utilisez la méthode **InferXmlSchema** et faites en sorte que l'espace de noms XML de **officedata** soit ignoré, comme le montre l'exemple suivant.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## Voir aussi  
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [Dérivation de la structure relationnelle d'un DataSet à partir d'un schéma XML \(XSD\)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)   
 [Inférence de la structure relationnelle d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [Chargement d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)