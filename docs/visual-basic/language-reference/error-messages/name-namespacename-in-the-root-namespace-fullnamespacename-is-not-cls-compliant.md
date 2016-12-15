---
title: "Name &lt;namespacename&gt; in the root namespace &lt;fullnamespacename&gt; is not CLS-compliant | Microsoft Docs"
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
  - "vbc40039"
  - "bc40039"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40039"
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Name &lt;namespacename&gt; in the root namespace &lt;fullnamespacename&gt; is not CLS-compliant
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Un assembly est marqué comme `<CLSCompliant(True)>`, mais un élément du nom de l'espace de noms racine commence par un trait de soulignement \(`_`\).  
  
 Un élément de programmation peut contenir un ou plusieurs traits de soulignement, mais pour être conforme à la [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), il ne doit pas commencer par un trait de soulignement.  Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Lorsque vous appliquez <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l'attribut la valeur `True` ou `False` pour indiquer la conformité ou la non\-conformité.  Il n'existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n'appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.  
  
 Par défaut, ce message est un avertissement.  Pour plus d'informations sur le masquage des avertissements ou le traitement des avertissements en tant qu'erreurs, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d'erreur :** BC40039  
  
### Pour corriger cette erreur  
  
-   S'il est nécessaire d'avoir la conformité CLS, modifiez le nom de l'espace de noms racine pour qu'aucun de ses éléments ne commence par un trait de soulignement.  
  
-   Si le nom de l'espace de noms doit rester inchangé, supprimez l'<xref:System.CLSCompliantAttribute> de l'assembly ou marquez\-le comme `<CLSCompliant(False)>`.  
  
## Voir aussi  
 [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [\/rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)   
 [Page Application, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)   
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3)