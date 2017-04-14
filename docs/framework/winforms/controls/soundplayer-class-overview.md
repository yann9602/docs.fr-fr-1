---
title: "Vue d&#39;ensemble de la classe SoundPlayer | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "lire des sons, de la classe SoundPlayer"
  - "SoundPlayer (classe), à propos de la classe SoundPlayer"
  - "lecture des sons"
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Vue d&#39;ensemble de la classe SoundPlayer
Le <xref:System.Media.SoundPlayer> classe vous permet d’inclure facilement des sons dans vos applications.  
  
 Le <xref:System.Media.SoundPlayer> classe peut lire des fichiers audio au format .wav, à partir d’une ressource ou d’emplacements UNC ou HTTP. En outre, les <xref:System.Media.SoundPlayer> classe vous permet de charger ou lire des sons de façon asynchrone.  
  
 Vous pouvez également utiliser le <xref:System.Media.SystemSounds> classe pour lire des sons système courants, y compris un signal sonore.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Propriétés couramment utilisées, méthodes et événements  
  
|Nom|Description|  
|----------|-----------------|  
|<xref:System.Media.SoundPlayer.SoundLocation%2A> propriété|Le chemin d’accès ou l’adresse Web du son. Les valeurs acceptables peuvent être UNC ou HTTP.|  
|<xref:System.Media.SoundPlayer.LoadTimeout%2A> propriété|Le nombre de millisecondes que votre programme attendra pour charger un son avant qu’il lève une exception. La valeur par défaut est 10 secondes.|  
|<xref:System.Media.SoundPlayer.IsLoadCompleted%2A> propriété|Valeur booléenne indiquant si le signal sonore a terminé son chargement.|  
|<xref:System.Media.SoundPlayer.Load%2A> (méthode)|Charge un son de façon synchrone.|  
|<xref:System.Media.SoundPlayer.LoadAsync%2A> (méthode)|Commence à charger un son de façon asynchrone. Lorsque le chargement est complet, il déclenche le <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> événement.|  
|<xref:System.Media.SoundPlayer.Play%2A> (méthode)|Lit le son spécifié dans le <xref:System.Media.SoundPlayer.SoundLocation%2A> ou <xref:System.Media.SoundPlayer.Stream%2A> propriété dans un nouveau thread.|  
|<xref:System.Media.SoundPlayer.PlaySync%2A> (méthode)|Lit le son spécifié dans le <xref:System.Media.SoundPlayer.SoundLocation%2A> ou <xref:System.Media.SoundPlayer.Stream%2A> propriété dans le thread actuel.|  
|<xref:System.Media.SoundPlayer.Stop%2A> (méthode)|Arrête tout son en cours de lecture.|  
|<xref:System.Media.SoundPlayer.LoadCompleted> événement|Déclenché après le chargement d’un son.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Media.SoundPlayer>   
 <xref:System.Media.SystemSounds>