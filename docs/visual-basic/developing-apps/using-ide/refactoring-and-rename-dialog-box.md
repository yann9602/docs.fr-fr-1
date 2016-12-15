---
title: "Refactorisation et bo&#238;te de dialogue Renommer (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.RenameSymbol"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "symboles, changement de nom"
  - "noms, changement de symbole"
  - "Renommer (boîte de dialogue)"
ms.assetid: 001d2d81-9bb6-4e8e-ae3a-20c0daaa3959
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Refactorisation et bo&#238;te de dialogue Renommer (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Utilisez la boîte de dialogue **Renommer** prédéfinie de Visual Basic pour renommer des identificateurs de votre code pour les symboles, tels que les champs, les variables locales, les méthodes, les espaces de noms, les propriétés et les types.  Vous pouvez ouvrir la boîte de dialogue **Renommer** en cliquant avec le bouton droit sur la déclaration d'élément.  
  
 **Nouveau nom**  
 Spécifie le nouveau nom de l'élément de code.  
  
 **Emplacement**  
 Identifie l'espace de noms dans lequel effectuer des recherches lors de l'exécution de l'opération de changement de nom.  
  
## Changements de nom  
 La boîte de dialogue **Renommer** effectue des changements de nom légèrement différents, selon le type d'élément renommé.  
  
|Type d'élément|Changement de nom|  
|--------------------|-----------------------|  
|Classe|Remplace toutes les déclarations et utilisations de la classe par le nouveau nom.  Pour les classes partielles, le changement de nom est répercuté dans l'ensemble des éléments.|  
|Champ|Remplace la déclaration et les utilisations du champ par le nouveau nom.|  
|Variable locale|Modifie la déclaration et les utilisations de la variable en fonction du nouveau nom.|  
|Méthode|Remplace le nom de la méthode et toutes les références à cette méthode par le nouveau nom.|  
|Espace de noms|Remplace le nom de l'espace de noms par le nouveau nom, dans la déclaration, dans toutes les instructions `Imports` et dans tous les noms complets.|  
|Propriété|Remplace la déclaration et les utilisations de la propriété par le nouveau nom.|  
  
## Refactorisation  
 Pour fournir une expérience de refactorisation complète, Visual Basic s'est associé à Developer Express Inc.  pour obtenir la prise en charge de la refactorisation.  Consultez [Refactor\!](http://go.microsoft.com/fwlink/?LinkId=155788) dans le centre de développement Visual Basic MSDN pour obtenir des détails supplémentaires sur la manière de télécharger cet outil.  Refactor\!  prend en charge plus de 15 fonctionnalités de refactorisation individuelles.  Cela inclut des opérations telles que la réorganisation des paramètres, l'extraction de la méthode, l'encapsulation de champ et la création de surcharge.  
  
## Voir aussi  
 [Using the Visual Basic Development Environment](../../../visual-basic/developing-apps/using-ide/using-the-visual-basic-development-environment.md)