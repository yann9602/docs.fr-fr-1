---
title: "&#39;&lt;classname&gt;&#39; is not CLS-compliant because the interface &#39;&lt;interfacename&gt;&#39; it implements is not CLS-compliant | Microsoft Docs"
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
  - "bc40029"
  - "vbc40029"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40029"
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;classname&gt;&#39; is not CLS-compliant because the interface &#39;&lt;interfacename&gt;&#39; it implements is not CLS-compliant
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une classe ou une interface est marquée comme `<CLSCompliant(True)>` lorsqu'elle dérive ou implémente un type qui est marqué comme `<CLSCompliant(False)>` ou qui n'est pas marqué.  
  
 Pour qu'une classe ou une interface soit conforme [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), toute sa hiérarchie d'héritage doit être conforme.  Cela signifie que chaque type dont elle hérite, directement ou indirectement, doit être conforme.  De même, si une classe implémente une ou plusieurs interfaces, elles doivent être conformes dans l'ensemble de leurs hiérarchies d'héritage.  
  
 Lorsque vous appliquez <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l'attribut la valeur `True` ou `False` pour indiquer la conformité ou la non\-conformité.  Il n'existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n'appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.  
  
 Par défaut, ce message est un avertissement.  Pour plus d'informations sur le masquage des avertissements ou le traitement des avertissements en tant qu'erreurs, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d'erreur :** BC40029  
  
### Pour corriger cette erreur  
  
-   Si la conformité CLS est requise, définissez ce type dans une hiérarchie d'héritage ou un modèle d'implémentation différent.  
  
-   Si ce type doit rester dans sa hiérarchie d'héritage ou dans son modèle d'implémentation actuel, supprimez l'<xref:System.CLSCompliantAttribute> de sa définition ou marquez\-le comme `<CLSCompliant(False)>`.  
  
## Voir aussi  
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3)