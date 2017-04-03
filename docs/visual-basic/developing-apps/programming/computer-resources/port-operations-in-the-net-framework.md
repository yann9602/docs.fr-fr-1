---
title: "Opérations relatives aux ports dans le .NET Framework avec Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 61b91fe5f3bb016bace838b9eeabb1a59190bfe9
ms.lasthandoff: 03/13/2017

---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Opérations relatives aux ports dans le .NET Framework avec Visual Basic
Vous pouvez accéder aux ports série de votre ordinateur par l’intermédiaire des classes [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] dans l’espace de noms <xref:System.IO.Ports?displayProperty=fullName>. La classe la plus importante, <xref:System.IO.Ports.SerialPort>, fournit un framework pour les E/S synchrones et pilotées par des événements, l’accès aux états d’épinglage et d’arrêt, et l’accès aux propriétés des pilotes série. Elle peut être incluse dans un wrapper d’objet <xref:System.IO.Stream>, accessible via la propriété <xref:System.IO.Ports.SerialPort.BaseStream%2A>. L’inclusion de <xref:System.IO.Ports.SerialPort> dans un wrapper d’objet <xref:System.IO.Stream> permet aux classes qui utilisent des flux d’accéder au port série. L’espace de noms contient des énumérations qui simplifient le contrôle des ports série.  
  
 La méthode <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> est le moyen le plus simple de créer un objet <xref:System.IO.Ports.SerialPort>.  
  
> [!NOTE]
>  Vous ne pouvez pas utiliser les classes [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] pour accéder directement aux autres types de ports, tels que les ports parallèles, les ports USB, etc.  
  
## <a name="enumerations"></a>Énumérations  
 Ce tableau répertorie et décrit les principales énumérations utilisées pour accéder à un port série :  
  
|Énumération|Description|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|Spécifie le protocole de contrôle utilisé pour établir une communication de port série pour un objet <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.Parity>|Spécifie le bit de parité pour un objet <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.SerialData>|Spécifie le type de caractère qui a été reçu sur le port série de l’objet <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.SerialError>|Spécifie les erreurs qui se produisent sur l’objet <xref:System.IO.Ports.SerialPort>|  
|<xref:System.IO.Ports.SerialPinChange>|Spécifie le type de modification effectuée sur l’objet <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.StopBits>|Spécifie le nombre de bits d’arrêt utilisé sur l’objet <xref:System.IO.Ports.SerialPort>.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 [Accès aux ports de l’ordinateur](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
