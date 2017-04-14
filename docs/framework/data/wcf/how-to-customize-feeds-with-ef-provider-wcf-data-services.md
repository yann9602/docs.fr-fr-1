---
title: "Proc&#233;dure&#160;: personnaliser des flux avec le fournisseur Entity Framework (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Services de données WCF, personnalisation"
  - "Services de données WCF, personnalisation de flux"
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: personnaliser des flux avec le fournisseur Entity Framework (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vous permet de personnaliser la sérialisation Atom dans une réponse du service de données pour pouvoir mapper les propriétés d'une entité aux éléments inutilisés définis dans le protocole AtomPub.  Cette rubrique montre comment définir des attributs de mappage pour les types d'entité dans un modèle de données défini dans un fichier .edmx à l'aide du fournisseur Entity Framework.  Pour plus d'informations, consultez [Personnalisation de flux](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
 Dans cette rubrique vous modifierez manuellement le fichier .edmx généré par un outil qui contient le modèle de données.  Vous devez modifier manuellement le fichier car les extensions vers le modèle de données ne sont pas prises en charge par le Concepteur d'entités.  Pour plus d'informations sur le fichier .edmx généré par les outils Entity Data Model, consultez [.edmx File Overview](http://msdn.microsoft.com/fr-fr/f4c8e7ce-1db6-417e-9759-15f8b55155d4).  L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement.  Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### Pour modifier manuellement le fichier Northwind.edmx pour ajouter des attributs de personnalisation de flux  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier `Northwind.edmx`, puis cliquez sur **Ouvrir avec**.  
  
2.  Dans la boîte de dialogue **Ouvrir avec\- Northwind.edmx**, sélectionnez **Éditeur XML**, puis cliquez sur **OK**.  
  
3.  Localisez l'élément `ConceptualModels` et remplacez le type d'entité `Customers` existant par l'élément suivant qui contient des attributs de mappage de personnalisation de flux :  
  
     [!code-xml[Astoria Custom Feeds#EdmFeedCustomers](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/northwind.csdl#edmfeedcustomers)]  
  
4.  Enregistrez les modifications et fermez le fichier Northwind.edmx.  
  
5.  \(Facultatif\) Cliquez avec le bouton droit sur le fichier Northwind.edmx puis cliquez sur **Exécuter un outil personnalisé**.  
  
     Cette opération régénère le fichier de couche objet qui peut être obligatoire.  
  
6.  Recompilez le projet.  
  
## Exemple  
 L'exemple précédent retourne le résultat suivant pour l'URI `http://myservice/` `Northwind.svc/Customers('ALFKI')`.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/edmfeedresult.xml#edmfeedresult)]  
  
## Voir aussi  
 [Fournisseur Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)