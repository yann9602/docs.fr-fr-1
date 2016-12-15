---
title: "Can&#39;t create necessary temporary file | Microsoft Docs"
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
  - "vbrID322"
dev_langs: 
  - "VB"
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Can&#39;t create necessary temporary file
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le lecteur contenant le répertoire spécifié par la variable d'environnement TEMP est plein ou la variable d'environnement TEMP spécifie un lecteur ou un répertoire non valide ou en lecture seule.  
  
### Pour corriger cette erreur  
  
1.  Supprimez des fichiers du lecteur, si celui\-ci est plein.  
  
2.  Spécifiez un lecteur différent dans la variable d'environnement TEMP.  
  
3.  Spécifiez un lecteur valide pour la variable d'environnement TEMP.  
  
4.  Supprimez la restriction en lecture seule du lecteur ou répertoire actuellement spécifié.  
  
## Voir aussi  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)