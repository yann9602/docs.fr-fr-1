---
title: "IEnumRAWINPUTDEVIC:Clone | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Clone (méthode)"
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# IEnumRAWINPUTDEVIC:Clone
Crée un autre énumérateur de périphérique d'entrée brut avec le même état que l'énumérateur actuel à itérer au sein de la même liste.  
  
## Syntaxe  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### Paramètres  
 `ppenum`  
  
 \[sortie\] Adresse de la variable de sortie recevant le pointeur d'interface [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md).  Si la méthode est infructueuse, la valeur de cette variable de sortie est indéfinie.  
  
## Valeur de propriété\/valeur de retour  
 HRESULT : cette méthode prend en charge les valeurs de retour standard E\_INVALIDARG, E\_OUTOFMEMORY et E\_UNEXPECTED.  
  
## Notes  
 Cette méthode rend possible l'enregistrement d'un point dans la séquence d'énumération afin de retourner plus tard à ce point.  L'appelant doit diffuser séparément ce nouvel énumérateur du premier énumérateur.