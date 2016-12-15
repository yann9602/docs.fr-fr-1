---
title: "Property let procedure not defined and property get procedure did not return an object | Microsoft Docs"
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
  - "vbrID451"
dev_langs: 
  - "VB"
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Property let procedure not defined and property get procedure did not return an object
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Certaines propriétés, méthodes et opérations ne peuvent s'appliquer qu'aux objets `Collection`.  Vous avez spécifié une opération ou une propriété ne s'appliquant qu'aux collections, mais l'objet n'est pas une collection.  
  
### Pour corriger cette erreur  
  
1.  Vérifiez l'orthographe du nom de l'objet ou de la propriété ou bien vérifiez que l'objet est un objet `Collection`.  
  
2.  Examinez la méthode `Add`utilisée pour ajouter l'objet à la collection afin d'être sûr que la syntaxe est correcte et que tous les identificateurs ont été orthographiés correctement.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Collection>