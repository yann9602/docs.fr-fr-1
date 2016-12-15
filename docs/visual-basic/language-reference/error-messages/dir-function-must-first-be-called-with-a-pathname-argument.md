---
title: "&#39;Dir&#39; function must first be called with a &#39;PathName&#39; argument | Microsoft Docs"
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
  - "vbrDIR_IllegalCall"
dev_langs: 
  - "VB"
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Dir&#39; function must first be called with a &#39;PathName&#39; argument
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Un appel initial à la fonction `Dir` n'inclut pas l'argument `PathName`.  Le premier appel à `Dir` doit inclure `PathName`, mais les appels suivants à `Dir` ne doivent pas inclure de paramètres permettant d'extraire l'élément suivant.  
  
### Pour corriger cette erreur  
  
1.  Fournissez un argument `PathName` dans l'appel de fonction.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>