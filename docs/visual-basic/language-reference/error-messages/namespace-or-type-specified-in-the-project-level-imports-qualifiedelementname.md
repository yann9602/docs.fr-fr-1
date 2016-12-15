---
title: "Namespace or type specified in the project-level Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found | Microsoft Docs"
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
  - "vbc40057"
  - "bc40057"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40057"
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Namespace or type specified in the project-level Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'espace de noms ou le type spécifié dans les Imports '\<NomÉlémentQualifié\>' au niveau du projet ne contient aucun membre public ou est introuvableVérifiez que l'espace de noms ou le type est défini et qu'il contient au moins un membre public.Vérifiez que le nom d'alias ne contient pas d'autres alias.  
  
 Une propriété Imports d'un projet spécifie un élément conteneur qui soit ne peut pas être recherché soit ne définit pas de membres `Public`.  
  
 Un *élément conteneur* peut être un espace de noms, une classe, une structure, un module, une interface ou une énumération.  L'élément conteneur contient des membres, comme des variables, des procédures ou d'autres éléments conteneur.  
  
 L'objectif de l'importation est de permettre à votre code d'accéder à des membres espace de noms ou type sans devoir les qualifier.  Votre projet peut également avoir besoin d'ajouter une référence à l'espace de noms ou au type.  Pour plus d'informations, consultez « Importation d'éléments conteneurs » dans [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Si le compilateur ne trouve pas l'élément conteneur spécifié, il ne peut pas résoudre les références qui l'utilisent.  S'il trouve l'élément mais que celui\-ci n'expose pas de membres `Public`, aucune référence ne peut aboutir.  Dans l'un et l'autre cas, l'importation de l'élément n'a aucun sens.  
  
 Vous pouvez utiliser le **Concepteur de projets** pour spécifier des éléments à importer.  Utilisez la section **Espaces de noms importés** de la page **Références**.  Vous pouvez ouvrir le **Concepteur de projets** en double\-cliquant sur l'icône **My Project** dans l'**Explorateur de solutions**.  
  
 **ID d'erreur :** BC40057  
  
### Pour corriger cette erreur  
  
1.  Ouvrez le **Concepteur de projets** et basculez vers la page **Référence**.  
  
2.  Dans la section **Espaces de noms importés**, vérifiez que l'élément conteneur est accessible à partir de votre projet.  
  
3.  Vérifiez que l'élément conteneur expose au moins un membre `Public`.  
  
## Voir aussi  
 [Page Références, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Public](../../../visual-basic/language-reference/modifiers/public.md)   
 [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)