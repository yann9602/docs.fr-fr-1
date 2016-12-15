---
title: "WriteOnly (Visual Basic) | Microsoft Docs"
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
  - "WriteOnly"
  - "vb.WriteOnly"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "write-only properties"
  - "WriteOnly keyword"
  - "sensitive data, protecting"
  - "properties [Visual Basic], write-only"
  - "sensitive data"
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# WriteOnly (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie qu'une propriété peut être écrite, mais pas lue.  
  
## Notes  
  
## Règles  
 **Contexte de déclaration.** Vous pouvez utiliser `WriteOnly` seulement au niveau du module.  Cela signifie que le contexte de déclaration pour une propriété `WriteOnly` doit être une classe, une structure ou un module, et ne peut pas être un fichier source, un espace de noms ou une procédure.  
  
 Vous pouvez déclarer une propriété en tant que `WriteOnly`, mais pas une variable.  
  
## Quand utiliser WriteOnly  
 Parfois vous souhaitez que le code utilisateur soit capable de définir une valeur, mais pas de découvrir ce qu'elle est.  Par exemple, les données sensibles, telles qu'un numéro d'immatriculation social ou un mot de passe, doivent être protégé de l'accès par tout composant qui n'a pas défini ces données.  Dans ces cas, vous pouvez utiliser une propriété `WriteOnly` pour définir la valeur.  
  
> [!IMPORTANT]
>  Lorsque vous définissez et utilisez une propriété `WriteOnly`, tenez compte des mesures de protection supplémentaires suivantes :  
  
-   **Substitution.** Si la propriété est membre d'une classe, sa valeur par défaut doit être [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) et ne la déclarez pas en tant que `Overridable` ou `MustOverride`.  Cela empêche une classe dérivée d'accéder de manière indésirable via une substitution.  
  
-   **Niveau d'accès.** Si vous stockez les données sensibles de la propriété dans une ou plusieurs variables, déclarez\-les en tant que [Private](../../../visual-basic/language-reference/modifiers/private.md) afin qu'aucun autre code ne puisse y accéder.  
  
-   **Chiffrement.** Stockez toutes les données sensibles sous forme chiffrée plutôt qu'en texte brut.  Si du code nuisible accède d'une façon ou d'une autre à la zone de mémoire, il est plus difficile d'utiliser les données.  Le chiffrement est également utile s'il s'avère nécessaire de sérialiser les données sensibles.  
  
-   **Réinitialisation.** Lorsque la classe, la structure ou le module définissant la propriété sont arrêtés, réinitialisez les données sensibles à leurs valeurs par défaut ou à d'autres valeurs sans signification.  Cela apporte une protection supplémentaire lorsque cette zone de mémoire est libérée pour l'accès général.  
  
-   **Persistance.** Si vous pouvez l'éviter, ne rendez pas persistante toute donnée sensible, par exemple sur un disque.  De la même façon, n'écrivez pas de données sensibles dans le Presse\-papiers.  
  
 Le modificateur `WriteOnly` peut être utilisé dans le contexte suivant :  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## Voir aussi  
 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)   
 [Private](../../../visual-basic/language-reference/modifiers/private.md)   
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)