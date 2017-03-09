---
title: "Variable &#39;&lt;variablename&gt;&#39; is used before it has been assigned a value | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc42104"
  - "BC42104"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42104"
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Variable &#39;&lt;variablename&gt;&#39; is used before it has been assigned a value
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

La variable '\<NomVariable\>' est utilisée avant qu'une valeur ne lui ait été assignée.Une exception de référence null peut se produire au moment de l'exécution.  
  
 Une application dispose d'au moins un chemin d'accès possible par l'intermédiaire de son code qui lit une variable avant qu'une valeur lui soit assignée.  
  
 Si une valeur n'a jamais été assignée à une variable, elle stocke la valeur par défaut pour son type de données.  Pour un type de données référence, cette valeur par défaut est [Nothing](../../../visual-basic/language-reference/nothing.md).  La lecture d'une variable de référence qui a la valeur `Nothing` peut générer une exception <xref:System.NullReferenceException> dans certains cas.  
  
 Par défaut, ce message est un avertissement.  Pour plus d'informations sur le masquage des avertissements ou le traitement des avertissements en tant qu'erreurs, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d'erreur :** BC42104  
  
### Pour corriger cette erreur  
  
-   Vérifiez votre logique de flux de contrôle et assurez\-vous que la variable a une valeur valide avant que le contrôle passe à une instruction qui la lit.  
  
-   Pour garantir que la variable a toujours une valeur valide, initialisez\-la dans le cadre de sa déclaration.  Consultez « Initialisation » dans [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## Voir aussi  
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Déclaration de variable](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Dépannage des variables](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)