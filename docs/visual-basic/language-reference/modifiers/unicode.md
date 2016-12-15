---
title: "Unicode (Visual Basic) | Microsoft Docs"
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
  - "vb.Unicode"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Unicode, external references"
  - "Declare statement, marshaling strings"
  - "Unicode keyword"
  - "Unicode, marshaling strings"
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Unicode (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie que Visual Basic doit marshaler toutes les chaînes en valeurs Unicode indépendamment du nom de la procédure externe qui est déclarée.  
  
 Lorsque vous appelez une procédure définie à l'extérieur de votre projet, le compilateur Visual Basic n'a pas accès aux informations dont il a besoin pour appeler la procédure correctement.  Ces informations incluent l'emplacement de la procédure, son identification, sa séquence d'appel et son type de retour ainsi que le jeu de caractères de chaîne qu'elle utilise.  L'[Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) crée une référence à une procédure externe et fournit ces informations nécessaires.  
  
 La partie `charsetmodifier` de l'instruction `Declare` fournit les informations de jeu de caractères pour marshaler des chaînes lors d'un appel à la procédure externe.  Elle affecte également la façon dont Visual Basic recherche le nom de la procédure externe dans le fichier externe.  Le modificateur `Unicode` spécifie que Visual Basic doit marshaler toutes les chaînes en valeurs Unicode et doit rechercher la procédure sans modifier son nom lors de la recherche.  
  
 Si aucun modificateur de jeu de caractères n'est spécifié, `Ansi` s'applique par défaut.  
  
## Notes  
 Le modificateur `Unicode` peut être utilisé dans le contexte suivant :  
  
 [Declare, instruction](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## Notes du développeur sur Smart Device  
 Ce mot clé n'est pas pris en charge.  
  
## Voir aussi  
 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)   
 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)   
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)