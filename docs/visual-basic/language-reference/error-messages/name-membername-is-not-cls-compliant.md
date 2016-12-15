---
title: "Name &lt;membername&gt; is not CLS-compliant | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40031"
  - "vbc40031"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40031"
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Name &lt;membername&gt; is not CLS-compliant
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Un assembly est marqué comme `<CLSCompliant(True)>` mais expose un membre portant un nom qui commence par un trait de soulignement \(`_`\).  
  
 Un élément de programmation peut contenir un ou plusieurs traits de soulignement, mais pour être conforme à la [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), il ne doit pas commencer par un trait de soulignement.  Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Lorsque vous appliquez <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l'attribut la valeur `True` ou `False` pour indiquer la conformité ou la non\-conformité.  Il n'existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n'appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.  
  
 Par défaut, ce message est un avertissement.  Pour plus d'informations sur le masquage des avertissements ou le traitement des avertissements en tant qu'erreurs, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d'erreur :** BC40031  
  
### Pour corriger cette erreur  
  
-   Si vous avez un contrôle sur le code source, modifiez le nom de membre afin qu'il ne commence pas par un trait de soulignement.  
  
-   S'il est nécessaire que le nom de membre reste inchangé, supprimez l'<xref:System.CLSCompliantAttribute> de sa définition ou marquez\-le comme `<CLSCompliant(False)>`.  Vous pouvez toujours marquer l'assembly comme `<CLSCompliant(True)>`.  
  
## Voir aussi  
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3)