---
title: "Port Operations in the .NET Framework with Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ports, Visual Basic"
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Port Operations in the .NET Framework with Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Vous pouvez accéder aux ports série de votre ordinateur par l'intermédiaire des classes [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] dans l'espace de noms <xref:System.IO.Ports?displayProperty=fullName>.  La classe la plus importante, <xref:System.IO.Ports.SerialPort>, fournit une infrastructure pour les E\/S synchrones et pilotées par événements, l'accès aux états de broche et d'arrêt et l'accès aux propriétés des pilotes de série.  Il peut être encapsulé dans un objet <xref:System.IO.Stream>, accessible via la propriété <xref:System.IO.Ports.SerialPort.BaseStream%2A>.  L'encapsulation de <xref:System.IO.Ports.SerialPort> dans un objet <xref:System.IO.Stream> permet au port série d'être accessible par les classes qui utilisent des flux.  L'espace de noms inclut des énumérations qui simplifient le contrôle des ports série.  
  
 La méthode la plus simple pour créer un objet <xref:System.IO.Ports.SerialPort> s'effectue via la méthode <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
> [!NOTE]
>  Vous ne pouvez pas utiliser les classes [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] pour accéder directement à d'autres types de ports, tels que les ports parrallèles, les ports USB, etc.  
  
## Énumérations  
 Ce tableau répertorie et décrit les principales énumérations utilisées pour accéder à un port série :  
  
|||  
|-|-|  
|Énumération|Description|  
|<xref:System.IO.Ports.Handshake>|Spécifie le protocole de contrôle utilisé pour établir une communication de port série pour un objet <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.Parity>|Spécifie le bit de parité pour un objet <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.SerialData>|Spécifie le type de caractère qui a été reçu sur le port série de l'objet <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.SerialError>|Spécifie les erreurs qui se produisent sur l'objet <xref:System.IO.Ports.SerialPort>|  
|<xref:System.IO.Ports.SerialPinChange>|Spécifie le type de modification qui s'est produit sur l'objet <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.StopBits>|Spécifie le nombre de bits d'arrêt utilisé sur l'objet <xref:System.IO.Ports.SerialPort>.|  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 [Accessing the Computer's Ports](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)