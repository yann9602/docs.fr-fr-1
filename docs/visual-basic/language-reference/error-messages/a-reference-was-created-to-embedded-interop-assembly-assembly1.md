---
title: "A reference was created to embedded interop assembly &#39;&lt;assembly1&gt;&#39; because of an indirect reference to that assembly from assembly &#39;&lt;assembly2&gt;&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc40059"
  - "bc40059"
helpviewer_keywords: 
  - "VBC40059"
  - "BC40059"
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# A reference was created to embedded interop assembly &#39;&lt;assembly1&gt;&#39; because of an indirect reference to that assembly from assembly &#39;&lt;assembly2&gt;&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Une référence a été créée pour l'assembly d'interopérabilité incorporé '\<assembly1\>' en raison d'une référence indirecte à cet assembly à partir de l'assembly '\<assembly2\>'.Modifiez la propriété « Incorporer les types interop » sur l'un et l'autre assembly.  
  
 Vous avez ajouté une référence à un assembly \(assembly1\) avec une valeur de propriété `Embed Interop Types` égale à `True`.  Cela indique au compilateur d'incorporer les informations de type d'interopérabilité de cet assembly.  Toutefois, le compilateur ne peut pas incorporer d'informations de type d'interopérabilité de cet assembly car un autre assembly que vous avez également référencé \(assembly2\) fait référence également à cet assembly \(assembly1\) et a la propriété `Embed Interop Types` définie à `False`.  
  
> [!NOTE]
>  L'affectation de la valeur `True` à la propriété `Embed Interop Types` d'une référence d'assembly revient à référence l'assembly en utilisant l'option `/link` pour le compilateur de ligne de commande.  
  
 **ID d'erreur :** BC40059  
  
### Pour traiter cet avertissement  
  
-   Pour incorporer des informations de type d'interopérabilité pour les deux assemblys, affectez à la propriété `Embed Interop Types` la valeur `True` pour toutes les références à assembly1.  
  
-   Pour supprimer cet avertissement, vous pouvez définir la propriété `Embed Interop Types` de assembly1 à la valeur `False`.  Dans ce cas, les informations de type d'interopérabilité sont fournies par un assembly PIA \(Primary Interop Assembly\).  
  
## Voir aussi  
 [\/link](../../../visual-basic/reference/command-line-compiler/link.md)   
 [Programming with Primary Interop Assemblies](http://msdn.microsoft.com/fr-fr/306fa1d6-0703-4004-9e93-d0a57f1be81e)