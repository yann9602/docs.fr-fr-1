---
title: "Ansi (Visual Basic) | Microsoft Docs"
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
  - "vb.Ansi"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Declare statement, marshaling strings"
  - "ANSI, Visual Basic"
  - "ANSI"
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ansi (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie que Visual Basic doit marshaler toutes les chaînes en valeurs ANSI \(American Standards Institute\) indépendamment du nom de la procédure externe qui est déclarée.  
  
 Lorsque vous appelez une procédure définie à l'extérieur de votre projet, le compilateur Visual Basic n'a pas accès aux informations requises pour appeler la procédure correctement.  Ces informations incluent l'emplacement de la procédure, son identification, sa séquence d'appel et son type de retour ainsi que le jeu de caractères de chaîne qu'elle utilise.  L'[Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) crée une référence à une procédure externe et fournit ces informations nécessaires.  
  
 La partie `charsetmodifier` de l'instruction `Declare` fournit les informations de jeu de caractères pour marshaler des chaînes lors d'un appel à la procédure externe.  Elle affecte également la façon dont Visual Basic recherche le nom de la procédure externe dans le fichier externe.  Le modificateur `Ansi` spécifie que Visual Basic doit marshaler toutes les chaînes en valeurs ANSI et doit rechercher la procédure sans modifier son nom lors de la recherche.  
  
 Si aucun modificateur de jeu de caractères n'est spécifié, `Ansi` s'applique par défaut.  
  
## Notes  
 Le modificateur `Ansi` peut être utilisé dans le contexte suivant :  
  
 [Declare, instruction](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## Notes du développeur sur Smart Device  
 Ce mot clé n'est pas pris en charge.  
  
## Voir aussi  
 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)   
 [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)   
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)