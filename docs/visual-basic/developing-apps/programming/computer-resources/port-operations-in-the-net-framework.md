---
title: "Opérations relatives aux ports dans le .NET Framework avec Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8db016461ea204eaf349a2c588670a237c9e583b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Opérations relatives aux ports dans le .NET Framework avec Visual Basic
Vous pouvez accéder aux ports série de votre ordinateur par l’intermédiaire des classes [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] dans l’espace de noms <xref:System.IO.Ports?displayProperty=nameWithType>. La classe la plus importante, <xref:System.IO.Ports.SerialPort>, fournit un framework pour les E/S synchrones et pilotées par événements, l’accès aux états d’épinglage et d’arrêt, et l’accès aux propriétés des pilotes séries. Elle peut être encapsulée dans un objet <xref:System.IO.Stream>, accessible par l’intermédiaire de la propriété <xref:System.IO.Ports.SerialPort.BaseStream%2A>. L’encapsulage de <xref:System.IO.Ports.SerialPort> dans un objet <xref:System.IO.Stream> permet aux classes qui utilisent des flux d’accéder au port série. L’espace de noms contient des énumérations qui simplifient le contrôle des ports série.  
  
 Le moyen le plus simple de créer un objet <xref:System.IO.Ports.SerialPort> consiste à utiliser la méthode <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
> [!NOTE]
>  Vous ne pouvez pas utiliser les classes [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pour accéder directement aux autres types de ports, tels que les ports parallèles, les ports USB, etc.  
  
## <a name="enumerations"></a>Énumérations  
 Ce tableau répertorie et décrit les principales énumérations utilisées pour accéder à un port série :  
  
|Énumération|Description|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|Spécifie le protocole de contrôle utilisé pour établir une communication de port série pour un objet <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.Parity>|Spécifie le bit de parité pour un objet <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.SerialData>|Spécifie le type de caractère qui a été reçu sur le port série de l’objet <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.SerialError>|Spécifie les erreurs qui se produisent sur l’objet <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.SerialPinChange>|Spécifie le type de changement qui s’est produit sur l’objet <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.StopBits>|Spécifie le nombre de bits d’arrêt utilisés sur l’objet <xref:System.IO.Ports.SerialPort>.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 [Accès aux ports de l’ordinateur](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
