---
title: "&#39;&lt;elementname&gt;&#39; is obsolete (Visual Basic Warning) | Microsoft Docs"
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
  - "vbc40008"
  - "bc40008"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40008"
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;elementname&gt;&#39; is obsolete (Visual Basic Warning)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une instruction essaie d'accéder à un élément de programmation qui a été marqué avec l'attribut <xref:System.ObsoleteAttribute> et la directive pour le traiter comme un avertissement.  
  
 Vous pouvez marquer les éléments de programmation comme n'étant plus utilisés en leur appliquant <xref:System.ObsoleteAttribute>.  Dans ce cas, vous pouvez affecter à la propriété <xref:System.ObsoleteAttribute.IsError%2A> de l'attribut la valeur `True` ou `False`.  Si vous affectez la valeur `True`, le compilateur traite une tentative d'utilisation de l'élément comme une erreur.  Si vous affectez la valeur `False` ou laissez la valeur par défaut `False`, le compilateur émet un avertissement en cas de tentative d'utilisation de l'élément.  
  
 Par défaut, ce message est un avertissement, car la propriété <xref:System.ObsoleteAttribute.IsError%2A> de <xref:System.ObsoleteAttribute> a la valeur `False`.  Pour plus d'informations sur le masquage des avertissements ou le traitement des avertissements en tant qu'erreurs, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d'erreur :** BC40008  
  
### Pour corriger cette erreur  
  
-   Assurez\-vous que le nom de l'élément est orthographié correctement dans la référence du code source.  
  
## Voir aussi  
 [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)