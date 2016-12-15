---
title: "Auto (Visual Basic) | Microsoft Docs"
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
  - "vb.Auto"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Auto keyword, external references"
  - "Declare statement, marshaling strings"
  - "Auto keyword"
  - "Auto keyword, marshaling strings"
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Auto (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie que Visual Basic doit marshaler les chaînes d'après les règles de .NET Framework selon le nom externe de la procédure externe déclarée.  
  
 Lorsque vous appelez une procédure définie à l'extérieur de votre projet, le compilateur Visual Basic n'a pas accès aux informations dont il a besoin pour appeler la procédure correctement.  Ces informations incluent l'emplacement de la procédure, son identification, sa séquence d'appel et son type de retour ainsi que le jeu de caractères de chaîne qu'elle utilise.  L'[Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) crée une référence à une procédure externe et fournit ces informations nécessaires.  
  
 La partie `charsetmodifier` de l'instruction `Declare` fournit les informations de jeu de caractères pour marshaler des chaînes lors d'un appel à la procédure externe.  Elle affecte également la façon dont Visual Basic recherche le nom de la procédure externe dans le fichier externe.  Le modificateur `Auto` spécifie que Visual Basic doit marshaler les chaînes d'après les règles de .NET Framework et qu'il doit déterminer le jeu de caractères de base de la plateforme d'exécution et éventuellement modifier le nom de procédure externe si la recherche initiale échoue.  Pour plus d'informations, consultez « Jeux de caractères » dans [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).  
  
 Si aucun modificateur de jeu de caractères n'est spécifié, `Ansi` s'applique par défaut.  
  
## Notes  
 Le modificateur `Auto` peut être utilisé dans le contexte suivant :  
  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## Notes du développeur sur Smart Device  
 Ce mot clé n'est pas pris en charge.  
  
## Voir aussi  
 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)   
 [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)   
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)