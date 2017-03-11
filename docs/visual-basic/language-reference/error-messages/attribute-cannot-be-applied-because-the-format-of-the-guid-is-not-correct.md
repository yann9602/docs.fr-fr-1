---
title: "&#39;&lt;attribute&gt;&#39; cannot be applied because the format of the GUID &#39;&lt;number&gt;&#39; is not correct | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc32500"
  - "bc32500"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32500"
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# &#39;&lt;attribute&gt;&#39; cannot be applied because the format of the GUID &#39;&lt;number&gt;&#39; is not correct
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Un bloc d'attributs `COMClassAttribute` spécifie un identificateur global unique \(GUID\) non conforme au format approprié pour un GUID.  `COMClassAttribute` utilise les GUID pour identifier de façon unique la classe, l'interface et l'événement de création.  
  
 Un GUID se compose de 16 octets, dont les huit premiers sont numériques et les huit derniers sont binaires.  Il est généré par les utilitaires Microsoft, tels que uuidgen.exe et est unique dans l'espace et le temps.  
  
 **ID d'erreur :** BC32500  
  
### Pour corriger cette erreur  
  
1.  Déterminez le GUID ou les GUID corrects nécessaires pour identifier l'objet COM.  
  
2.  Assurez\-vous que les chaînes du GUID présentées au bloc d'attributs `COMClassAttribute` ont été copiées correctement.  
  
## Voir aussi  
 <xref:System.Guid>   
 [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)