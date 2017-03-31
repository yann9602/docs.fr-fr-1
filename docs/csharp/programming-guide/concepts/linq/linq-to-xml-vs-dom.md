---
title: "LINQ to XML, différences par rapport à DOM (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4734d82ef2f912e76a2e7a3dbc4ab3a2f45382b1
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-vs-dom-c"></a>LINQ to XML, différences par rapport à DOM (C#)
Cette section décrit certaines des principales différences entre [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] et l’API de programmation XML actuellement prédominante, le modèle DOM (Document Object Model) W3C.  
  
## <a name="new-ways-to-construct-xml-trees"></a>Nouvelles manières de construire des arborescences XML  
 Dans le modèle DOM W3C, vous construisez une arborescence XML de bas en haut ; autrement dit, vous créez un document, vous créez des éléments, puis vous ajoutez les éléments au document.  
  
 Voici un exemple typique de création d’une arborescence XML à l’aide de l’implémentation Microsoft du modèle DOM, <xref:System.Xml.XmlDocument> :  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
XmlElement phone1 = doc.CreateElement("Phone");  
phone1.SetAttribute("Type", "Home");  
phone1.InnerText = "206-555-0144";          
XmlElement phone2 = doc.CreateElement("Phone");  
phone2.SetAttribute("Type", "Work");  
phone2.InnerText = "425-555-0145";          
XmlElement street1 = doc.CreateElement("Street1");          
street1.InnerText = "123 Main St";  
XmlElement city = doc.CreateElement("City");  
city.InnerText = "Mercer Island";  
XmlElement state = doc.CreateElement("State");  
state.InnerText = "WA";  
XmlElement postal = doc.CreateElement("Postal");  
postal.InnerText = "68042";  
XmlElement address = doc.CreateElement("Address");  
address.AppendChild(street1);  
address.AppendChild(city);  
address.AppendChild(state);  
address.AppendChild(postal);  
XmlElement contact = doc.CreateElement("Contact");  
contact.AppendChild(name);  
contact.AppendChild(phone1);  
contact.AppendChild(phone2);  
contact.AppendChild(address);  
XmlElement contacts = doc.CreateElement("Contacts");  
contacts.AppendChild(contact);  
doc.AppendChild(contacts);  
```  
  
 Ce style de codage ne fournit visuellement que peu d’informations concernant la structure de l’arborescence XML. [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] prend en charge cette approche de la construction d’une arborescence XML, mais également une approche alternative, la *construction fonctionnelle*. La construction fonctionnelle utilise les constructeurs <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XAttribute> pour créer une arborescence XML.  
  
 Voici comment vous pouvez construire la même arborescence XML à l’aide de la construction fonctionnelle [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] :  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144",   
                new XAttribute("Type", "Home")),  
            new XElement("phone", "425-555-0145",  
                new XAttribute("Type", "Work")),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 Notez que la mise en retrait du code pour construire l’arborescence XML affiche la structure des données XML sous-jacentes.  
  
 Pour plus d’informations, consultez [Création d’arborescences XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="working-directly-with-xml-elements"></a>Utilisation directe des éléments XML  
 Lorsque vous programmez avec des données XML, vous travaillez en général principalement avec les éléments XML et éventuellement les attributs. Dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], vous pouvez utiliser directement les éléments et les attributs XML. Vous pouvez par exemple effectuer les opérations suivantes :  
  
-   Créer des éléments XML sans utiliser d'objet de document. Cela simplifie la programmation lorsque vous devez travailler avec des fragments d'arborescences XML.  
  
-   Charger des objets `T:System.Xml.Linq.XElement` directement à partir d'un fichier XML.  
  
-   Sérialiser des objets `T:System.Xml.Linq.XElement` dans un fichier ou un flux.  
  
 Comparez cela au modèle DOM W3C, dans lequel le document XML est utilisé en tant que conteneur logique pour l'arborescence XML. Dans le modèle DOM, les nœuds XML, y compris les éléments et attributs, doivent être créés dans le contexte d'un document XML. Voici un fragment de code permettant de créer un élément de nom dans le modèle DOM :  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 Si vous souhaitez utiliser un élément dans plusieurs documents, vous devez importer les nœuds d'un document à un autre. [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] évite cette couche de complexité.  
  
 Lors de l’utilisation de LINQ to XML, vous utilisez la classe <xref:System.Xml.Linq.XDocument> seulement si vous voulez ajouter un commentaire ou une instruction de traitement au niveau racine du document.  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>Gestion simplifiée des noms et des espaces de noms  
 La gestion des noms, des espaces de noms et des préfixes d'espaces de noms est généralement un aspect complexe de la programmation XML. [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] simplifie les noms et les espaces de noms en éliminant la nécessité de gérer les préfixes d’espaces de noms. Vous pouvez si vous le souhaitez contrôler les préfixes d'espaces de noms. Si vous décidez cependant de ne pas contrôler explicitement les préfixes d’espaces de noms, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] affecte des préfixes d’espaces de noms lors de la sérialisation s’ils sont nécessaires ou, s’ils ne le sont pas, sérialise en utilisant les espaces de noms par défaut. Si des espaces de noms par défaut sont utilisés, il n'y aura pas de préfixes d'espaces de noms dans le document résultant. Pour plus d’informations, consultez [Utilisation des espaces de noms XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 L'un des autres problèmes associés au modèle DOM est qu'il ne vous permet pas de modifier le nom d'un nœud. Au lieu de cela, vous devez créer un nouveau nœud et y copier tous les nœuds enfants, perdant ainsi l'identité de nœud d'origine. [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] évite ce problème en vous permettant de définir la propriété <xref:System.Xml.Linq.XName> sur un nœud.  
  
## <a name="static-method-support-for-loading-xml"></a>Prise en charge des méthodes statiques pour le chargement de données XML  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] vous permet de charger du code XML en utilisant des méthodes statiques au lieu de méthodes d’instance. Cela simplifie le chargement et l'analyse. Pour plus d’informations, consultez [Guide pratique pour charger du code XML à partir d’un fichier (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).  
  
## <a name="removal-of-support-for-dtd-constructs"></a>Suppression de la prise en charge des constructions de DTD  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] simplifie la programmation XML en supprimant la prise en charge des entités et des références d'entités. La gestion des entités est complexe et rarement utilisée. La suppression de leur prise en charge augmente les performances et simplifie l'interface de programmation. Quand une arborescence [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] est remplie, toutes les entités DTD sont développées.  
  
## <a name="support-for-fragments"></a>Prise en charge des fragments  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] ne fournit pas d’équivalent pour la classe `XmlDocumentFragment`. Cependant, dans de nombreux cas, le concept `XmlDocumentFragment` peut être géré par le résultat d’une requête typée comme <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XNode> ou <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>.  
  
## <a name="support-for-xpathnavigator"></a>Prise en charge de XPathNavigator  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] fournit la prise en charge de <xref:System.Xml.XPath.XPathNavigator> via les méthodes d’extension dans l’espace de noms <xref:System.Xml.XPath?displayProperty=fullName>. Pour plus d’informations, consultez <xref:System.Xml.XPath.Extensions?displayProperty=fullName>.  
  
## <a name="support-for-white-space-and-indentation"></a>Prise en charge des espaces blancs et de la mise en retrait  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] gère les espaces plus simplement que le modèle DOM.  
  
 Un scénario courant consiste à lire le code XML mis en retrait, à créer une arborescence XML en mémoire sans nœuds d'espaces (autrement dit, ne pas conserver les espaces), à effectuer certaines opérations sur le code XML, puis à enregistrer le code XML avec mise en retrait. Lorsque vous sérialisez le code XML avec mise en forme, seuls les espaces significatifs dans l'arborescence XML sont conservés. Il s'agit du comportement par défaut pour [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
 Un autre scénario courant consiste à lire et à modifier du code XML qui a déjà été intentionnellement mis en retrait. Vous ne souhaiterez peut-être modifier cette mise en retrait en aucune manière. Dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], vous devez pour cela conserver les espaces lorsque vous chargez ou analysez le code XML et que vous désactivez la mise en forme lors de la sérialisation du code XML.  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] stocke un espace sous la forme d’un nœud <xref:System.Xml.Linq.XText>, au lieu d’utiliser un type de nœud <xref:System.Xml.XmlNodeType> spécialisé, comme le fait le modèle DOM.  
  
## <a name="support-for-annotations"></a>Prise en charge des annotations  
 Les éléments [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] prennent en charge un ensemble extensible d'annotations. Cela est utile pour assurer le suivi de diverses informations relatives à un élément, telles que des informations de schéma, le fait que l'élément soit lié à une interface utilisateur ou tout autre type d'informations spécifiques aux applications. Pour plus d’informations, consultez [Annotations LINQ to XML](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).  
  
## <a name="support-for-schema-information"></a>Prise en charge des informations de schéma  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] fournit la prise en charge de la validation XSD via des méthodes d’extension dans l’espace de noms <xref:System.Xml.Schema?displayProperty=fullName>. Vous pouvez valider la conformité d’une arborescence XML à un schéma XSD. Vous pouvez remplir l’arborescence XML avec le PSVI (Post-Schema-Validation Infoset). Pour plus d’informations, consultez [Comment : valider à l’aide de XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) et <xref:System.Xml.Schema.Extensions>.  
  
## <a name="see-also"></a>Voir aussi  
 [Bien démarrer (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
