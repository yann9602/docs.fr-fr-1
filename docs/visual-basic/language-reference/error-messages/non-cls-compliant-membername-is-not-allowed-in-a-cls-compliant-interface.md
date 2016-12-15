---
title: "Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface | Microsoft Docs"
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
  - "bc40033"
  - "vbc40033"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40033"
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une propriété, une procédure ou un événement dans une interface est marquée comme `<CLSCompliant(True)>` lorsque l'interface proprement dite est marquée comme `<CLSCompliant(False)>` ou n'est pas marquée.  
  
 Pour qu'une interface soit conforme au [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), tous ses membres doivent être conformes.  
  
 Lorsque vous appliquez <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l'attribut la valeur `True` ou `False` pour indiquer la conformité ou la non\-conformité.  Il n'existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n'appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.  
  
 Par défaut, ce message est un avertissement.  Pour plus d'informations sur le masquage des avertissements ou le traitement des avertissements en tant qu'erreurs, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d'erreur :** BC40033  
  
### Pour corriger cette erreur  
  
-   Si la conformité CLS est requise et si vous avez le contrôle du code source de l'interface, marquez l'interface comme `<CLSCompliant(True)>` si tous ses membres sont conformes.  
  
-   Si la conformité CLS est requise et si vous n'avez pas le contrôle du code source de l'interface ou si elle n'est pas considérée comme conforme, définissez ce membre dans une autre interface.  
  
-   Si ce membre doit rester dans son interface actuelle, supprimez <xref:System.CLSCompliantAttribute> de sa définition ou marquez\-le comme `<CLSCompliant(False)>`.  
  
## Voir aussi  
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3)