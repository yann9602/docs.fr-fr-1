---
title: "Proc&#233;dure&#160;: ex&#233;cuter une requ&#234;te qui retourne des types complexes | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "ESQL"
  - "jsharp"
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: ex&#233;cuter une requ&#234;te qui retourne des types complexes
Cette rubrique indique comment exécuter une requête [!INCLUDE[esql](../../../../../includes/esql-md.md)] qui retourne des objets de type d'entité qui contiennent une propriété d'un type complexe.  
  
### Pour exécuter le code de cet exemple  
  
1.  Ajoutez le [AdventureWorks Sales Model](http://msdn.microsoft.com/fr-fr/f16cd988-673f-4376-b034-129ca93c7832) à votre projet et configurez votre projet pour utiliser [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Pour plus d'informations, consultez [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/fr-fr/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Dans la page de codes de votre application, ajoutez les instructions `using` \(`Imports` en Visual Basic\) suivantes :  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  Double\-cliquez sur le fichier .edmx pour afficher le modèle dans la [fenêtre Explorateur de modèles](http://msdn.microsoft.com/fr-fr/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) du Concepteur d'entités.  Sur l'aire du Concepteur d'entités, sélectionnez les propriétés `Email` et `Phone` du type d'entité `Contact`, puis cliquez avec le bouton droit et sélectionnez **Refactoriser en nouveau type complexe**.  
  
4.  Un nouveau type complexe avec les propriétés `Email` et `Phone` sélectionnées est ajouté à l'**Explorateur de modèles**.  Le type complexe reçoit un nom par défaut : renommez le type en `EmailPhone` dans la fenêtre **Propriétés**.  Une nouvelle propriété `ComplexProperty` est également ajoutée au type d'entité `Contact`.  Renommez la propriété en `EmailPhoneComplexType.`.  
  
     Pour plus d'informations sur la création et la modification de types complexes à l'aide de l'Assistant EDM, consultez [How to: Refactor Existing Properties into a Complex Type Property](http://msdn.microsoft.com/fr-fr/5b2eb3b3-693d-42cb-b43a-405812d677eb) et[How to: Create and Modify Complex Types](http://msdn.microsoft.com/fr-fr/afb8e206-0ffe-4597-b6d4-6ab566897e1d).  
  
## Exemple  
 L'exemple suivant exécute une requête qui retourne une collection d'objets `Contact` et affiche deux propriétés des objets `Contact`  objets : `ContactID` et les valeurs du type complexe `EmailPhoneComplexType`.  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]