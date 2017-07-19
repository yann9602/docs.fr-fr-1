---
title: "Synchronisation des objets DataSet et XmlDataDocument | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Synchronisation des objets DataSet et XmlDataDocument
L'objet <xref:System.Data.DataSet> ADO.NET vous propose une représentation relationnelle des données.  Pour un accès hiérarchique aux données, vous pouvez utiliser les classes XML disponibles dans le .NET Framework.  Pour des raisons historiques, ces deux représentations des données ont jusqu'à présent été utilisées séparément.  Toutefois, le .NET Framework permet un accès synchrone et en temps réel aux représentations relationnelles et hiérarchiques des données, via respectivement l'objet **DataSet** et l'objet <xref:System.Xml.XmlDataDocument>.  
  
 Lorsqu'un **DataSet** est synchronisé avec un **XmlDataDocument**, les deux objets utilisent un même groupe de données.  Cela signifie que si une modification est apportée au **DataSet**, elle sera répercutée dans le **XmlDataDocument** et vice versa.  La relation entre le **DataSet** et le **XmlDataDocument** autorise une grande souplesse, puisqu'une même application peut, en utilisant le même groupe de données, accéder à l'ensemble des services construits autour du **DataSet** \(comme les contrôles Web Forms et Windows Forms ou les concepteurs Visual Studio .NET\), ainsi qu'à la suite de services XML, dont XSL \(Extensible Stylesheet Language\), XSLT \(XSL Transformations\) et XPath \(XML Path Language\).  Vous n'avez pas à choisir l'ensemble de services que l'application devra utiliser, puisque les deux sont disponibles.  
  
 Vous pouvez synchroniser un **DataSet** avec un **XmlDataDocument** de différentes manières.  Vous pouvez :  
  
-   Remplir un **DataSet** avec un schéma \(c'est\-à\-dire une structure relationnelle\) et des données, puis le synchroniser avec un nouveau **XmlDataDocument**.  Vous obtenez ainsi une vue hiérarchique des données relationnelles existantes.  Par exemple :  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema and data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema and data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    ```  
  
-   Remplir un **DataSet** avec un schéma uniquement \(comme un **DataSet** fortement typé\), le synchroniser avec un **XmlDataDocument**, puis charger le **XmlDataDocument** à partir d'un document XML.  Vous obtenez ainsi une vue relationnelle des données hiérarchiques existantes.  Les noms des tables et des colonnes de votre schéma **DataSet** doivent correspondre à ceux des éléments XML avec lesquels vous voulez les synchroniser.  Cette mise en correspondance respecte la casse.  
  
     Notez que le schéma du **DataSet** ne doit établir de correspondance que pour les éléments XML que vous souhaitez exposer dans votre vue relationnelle.  De cette façon, vous pouvez disposer d'un document XML très volumineux et d'une toute petite « fenêtre » relationnelle sur ce document.  Le **XmlDataDocument** conserve l'intégralité du document XML, même si le **DataSet** n'en expose qu'une petite partie  \(pour obtenir un exemple détaillé, voir [Synchronisation d'un DataSet avec un XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)\).  
  
     L'exemple de code suivant illustre les étapes nécessaires à la création d'un **DataSet** et au remplissage de son schéma, puis à sa synchronisation avec un **XmlDataDocument**.  Notez que le schéma du **DataSet** ne doit établir de correspondance que pour les éléments du **XmlDataDocument** que vous souhaitez exposer à l'aide du **DataSet**.  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema, but not data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema, but not data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
     Vous ne pouvez pas charger un **XmlDataDocument** s'il est synchronisé avec un **DataSet** qui contient des données.  Une exception sera levée.  
  
-   Créer un nouveau **XmlDataDocument** et le charger à partir d'un document XML, puis accéder à la vue relationnelle des données à l'aide de la propriété **DataSet** du **XmlDataDocument**.  Vous devrez définir le schéma du **DataSet** avant de pouvoir afficher des données dans le **XmlDataDocument** à l'aide du **DataSet**.  Là encore, les noms des tables et des colonnes de votre schéma **DataSet** doivent correspondre à ceux des éléments XML avec lesquels vous voulez les synchroniser.  Cette mise en correspondance respecte la casse.  
  
     L'exemple de code suivant montre comment accéder à la vue relationnelle des données d'un **XmlDataDocument**.  
  
    ```vb  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument  
    Dim dataSet As DataSet = xmlDoc.DataSet  
  
    ' Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml")  
  
    ```  
  
    ```csharp  
    XmlDataDocument xmlDoc = new XmlDataDocument();  
    DataSet dataSet = xmlDoc.DataSet;  
  
    // Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
 La synchronisation d'un **XmlDataDocument** avec un **DataSet** présente aussi l'avantage de préserver la fidélité d'un document XML.  Si le **DataSet** est rempli à partir d'un document XML à l'aide de **ReadXml**, lorsque les données sont réécrites sous forme de document XML à l'aide de **WriteXml**, le document XML obtenu peut considérablement différer de l'original.  En effet, le **DataSet** ne conserve ni la mise en forme, comme un espace blanc, ni les informations hiérarchiques, comme l'ordre des éléments, du document XML.  Le **DataSet** ne contient pas non plus les éléments du document XML qui ont été ignorés parce qu'ils ne correspondaient pas au schéma du **DataSet**.  Synchroniser un **XmlDataDocument** avec un **DataSet** permet de préserver la mise en forme et la structure hiérarchique des éléments du document XML d'origine dans le **XmlDataDocument**, alors que le **DataSet** ne contient que des données et les informations de schéma appropriées pour le **DataSet**.  
  
 Les résultats d'une synchronisation d'un **DataSet** avec un **XmlDataDocument** peuvent varier selon que vos objets <xref:System.Data.DataRelation> sont ou non imbriqués.  Pour plus d'informations, consultez [Imbrication de DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
## Dans cette section  
 [Synchronisation d'un DataSet avec un XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 Présente un **DataSet** fortement typé, avec un schéma minimal, en cours de synchronisation avec un **XmlDataDocument**.  
  
 [Exécution d'une requête XPath sur un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 Présente l'exécution d'une requête XPath sur le contenu d'un **DataSet**.  
  
 [Application d'une transformation XSLT à un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 Présente l'application d'une transformation XSLT au contenu d'un **DataSet**.  
  
## Rubriques connexes  
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Explique comment le **DataSet** interagit avec XML en tant que source de données, notamment en ce qui concerne le chargement et la persistance du contenu d'un **DataSet** en tant que données XML.  
  
 [Imbrication de DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 Explique l'importance des objets **DataRelation** imbriqués lorsqu'il s'agit de représenter le contenu d'un **DataSet** sous forme de données XML, et décrit la façon de les créer.  
  
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Décrit le **DataSet** et la façon de l'utiliser pour gérer des données d'application et interagir avec des sources de données incluant des bases de données relationnelles et XML.  
  
 [Classe XmlDataDocument](frlrfSystemXmlXmlDataDocumentClassTopic)  
 Contient des informations de référence sur la classe **XmlDataDocument**.  
  
## Voir aussi  
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)