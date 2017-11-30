---
title: "Intégration de XML aux données relationnelles et à ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6ebb1a1-f2ca-49b9-92c9-0150940cf6e6
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5d03a0ca7518b06c08d98967d7c5ae864f1c04ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-integration-with-relational-data-and-adonet"></a>Intégration de XML aux données relationnelles et à ADO.NET
Le **XmlDataDocument** classe est une classe dérivée de la **XmlDocument**et contient des données XML. L’avantage de la **XmlDataDocument** est qu’il fournit un pont entre les données relationnelles et hiérarchiques. Il s’agit d’un **XmlDocument** qui peut être lié à un **DataSet** et les deux classes peuvent synchroniser des changements apportés aux données contenues dans ces deux classes. Un **XmlDocument** qui est lié à un **DataSet** permet d’intégrer des données relationnelles XML, et vous n’êtes pas obligé de vos données représentées sous la forme d’un XML ou dans un format relationnel. Vous pouvez effectuer les deux sans être limité à une représentation unique des données.  
  
 Les avantages d'avoir les données disponibles sous deux vues sont les suivants :  
  
-   La portion structurée d'un document XML peut être mappée à un groupe de données et peut être stockée, indexée et recherchée efficacement.  
  
-   Transformations, validation et navigation peuvent s’effectuer de manière efficace par l’intermédiaire d’un modèle de curseur sur les données XML stockées de manière relationnelle. Dans certains cas, il peut être effectué plus efficacement par rapport à des structures relationnelles que si le XML est stocké dans un **XmlDocument** modèle.  
  
-   Le **DataSet** peut stocker une portion du XML. Autrement dit, vous pouvez utiliser **XPath** ou **XslTransform** pour ne stocker dans un **DataSet** que les éléments et attributs présentant un intérêt. À partir de là, les modifications peuvent être apportées au sous-ensemble plus petit et filtré de données, avec les changements se propageant aux données plus volumineuses dans le **XmlDataDocument**.  
  
 Vous pouvez également exécuter une transformation sur des données a été chargées dans le **DataSet** à partir de SQL Server. Une autre option consiste à lier WinForm managés par style de classes de .NET Framework et des contrôles WebForm un **DataSet** qui a été rempli à partir d’un flux d’entrée XML.  
  
 Prise en charge de **XslTransform**, un **XmlDataDocument** expose des données relationnelles à **XPath** requêtes et validation.  Autrement dit, tous les services XML sont disponibles pour les données relationnelles, et les fonctionnalités relationnelles, comme la liaison de contrôle, codegen, etc., sont disponibles sur une projection structurée de XML sans compromettre la fidélité du XML.  
  
 Étant donné que **XmlDataDocument** est héritée d’un **XmlDocument**, il fournit une implémentation du DOM W3C. Le fait qui le **XmlDataDocument** est associé et stocke un sous-ensemble de ses données dans un **DataSet** ne restreint ou ne modifie son utilisation comme un **XmlDocument** en aucune façon. Le code écrit pour consommer un **XmlDocument** fonctionne sans altération par rapport à un **XmlDataDocument**. Le **DataSet** fournit la vue relationnelle des mêmes données en définissant des tables, colonnes, relations et contraintes, et est un magasin de données utilisateur autonome, en mémoire.  
  
 L’illustration suivante montre les différentes associations que les données XML entretiennent avec les **DataSet** et **XmlDataDocument**.  
  
 ![Jeu de données XML](../../../../docs/standard/data/xml/media/xmlintegrationwithrelationaldataandadodotnet.gif "xmlIntegrationWithRelationalDataAndADOdotNet")  
  
 L’illustration montre que les données XML peuvent être chargées directement dans un **DataSet**, ce qui permet une manipulation directe avec XML de la manière relationnelle. Ou bien, le XML peut être chargé dans une classe dérivée du DOM, qui est la **XmlDataDocument**, puis ensuite être chargé et synchronisé avec le **DataSet**. Étant donné que la **DataSet** et **XmlDataDocument** sont synchronisés sur un seul jeu de données, les modifications apportées aux données dans un magasin sont reflétées dans l’autre magasin.  
  
 Le **XmlDataDocument** hérite de toutes les fonctionnalités de modification et de navigation à partir de la **XmlDocument**. Il se peut que lorsque vous utilisez la **XmlDataDocument** et ses fonctionnalités héritées, synchronisées avec un **DataSet**, est une option plus appropriée que le chargement de XML directement dans le **DataSet**. Le tableau suivant présente les éléments à prendre en considération lors du choix de la méthode à utiliser pour charger le **DataSet**.  
  
|Exemple de chargement du XML directement dans un DataSet|Exemple de synchronisation d’un DataSet avec un XmlDataDocument|  
|----------------------------------------------|-----------------------------------------------------------|  
|Les requêtes de données dans le **DataSet** sont plus faciles à l’aide de SQL que de XPath.|Les requêtes XPath sont nécessaires sur les données dans le **DataSet**.|  
|La préservation de l'ordre des éléments dans le XML source n'est pas critique.|La préservation de l'ordre des éléments dans le XML source est critique.|  
|Il n'est pas nécessaire de préserver l'espace blanc entre des éléments et la mise en forme dans le XML source.|La préservation des espaces blancs et de la mise en forme dans le XML source est critique.|  
  
 Si le chargement et l’écriture de XML directement dans et hors d’un **DataSet** répond à vos besoins, consultez [chargement d’un DataSet à partir de XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) et [l’écriture d’un DataSet sous forme de données XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Si le chargement du **DataSet** d’une **XmlDataDocument** répond à vos besoins, consultez [synchronisation d’un DataSet avec un Document XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de XML dans un DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
