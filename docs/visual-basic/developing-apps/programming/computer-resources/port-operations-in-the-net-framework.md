---
title: "Opérations relatives aux ports dans le .NET Framework avec Visual Basic"
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
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e01853cba19ffa0a7d9997eef3d25d2b2e3166dd
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="978ea-102">Opérations relatives aux ports dans le .NET Framework avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="978ea-102">Port Operations in the .NET Framework with Visual Basic</span></span>
<span data-ttu-id="978ea-103">Vous pouvez accéder aux ports série de votre ordinateur par l’intermédiaire des classes [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] dans l’espace de noms <xref:System.IO.Ports?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="978ea-103">You can access your computer's serial ports through the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes in the <xref:System.IO.Ports?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="978ea-104">La classe la plus importante, <xref:System.IO.Ports.SerialPort>, fournit un framework pour les E/S synchrones et pilotées par événements, l’accès aux états d’épinglage et d’arrêt, et l’accès aux propriétés des pilotes séries.</span><span class="sxs-lookup"><span data-stu-id="978ea-104">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="978ea-105">Elle peut être encapsulée dans un objet <xref:System.IO.Stream>, accessible par l’intermédiaire de la propriété <xref:System.IO.Ports.SerialPort.BaseStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="978ea-105">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream%2A> property.</span></span> <span data-ttu-id="978ea-106">L’encapsulage de <xref:System.IO.Ports.SerialPort> dans un objet <xref:System.IO.Stream> permet aux classes qui utilisent des flux d’accéder au port série.</span><span class="sxs-lookup"><span data-stu-id="978ea-106">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="978ea-107">L’espace de noms contient des énumérations qui simplifient le contrôle des ports série.</span><span class="sxs-lookup"><span data-stu-id="978ea-107">The namespace includes enumerations that simplify the control of serial ports.</span></span>  
  
 <span data-ttu-id="978ea-108">Le moyen le plus simple de créer un objet <xref:System.IO.Ports.SerialPort> consiste à utiliser la méthode <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="978ea-108">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="978ea-109">Vous ne pouvez pas utiliser les classes [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pour accéder directement aux autres types de ports, tels que les ports parallèles, les ports USB, etc.</span><span class="sxs-lookup"><span data-stu-id="978ea-109">You cannot use [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>  
  
## <a name="enumerations"></a><span data-ttu-id="978ea-110">Énumérations</span><span class="sxs-lookup"><span data-stu-id="978ea-110">Enumerations</span></span>  
 <span data-ttu-id="978ea-111">Ce tableau répertorie et décrit les principales énumérations utilisées pour accéder à un port série :</span><span class="sxs-lookup"><span data-stu-id="978ea-111">This table lists and describes the main enumerations used for accessing a serial port:</span></span>  
  
|<span data-ttu-id="978ea-112">Énumération</span><span class="sxs-lookup"><span data-stu-id="978ea-112">Enumeration</span></span>|<span data-ttu-id="978ea-113">Description</span><span class="sxs-lookup"><span data-stu-id="978ea-113">Description</span></span>|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="978ea-114">Spécifie le protocole de contrôle utilisé pour établir une communication de port série pour un objet <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="978ea-114">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="978ea-115">Spécifie le bit de parité pour un objet <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="978ea-115">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="978ea-116">Spécifie le type de caractère qui a été reçu sur le port série de l’objet <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="978ea-116">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="978ea-117">Spécifie les erreurs qui se produisent sur l’objet <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="978ea-117">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|  
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="978ea-118">Spécifie le type de changement qui s’est produit sur l’objet <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="978ea-118">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="978ea-119">Spécifie le nombre de bits d’arrêt utilisés sur l’objet <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="978ea-119">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="978ea-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="978ea-120">See Also</span></span>  
 <span data-ttu-id="978ea-121"><xref:Microsoft.VisualBasic.Devices.Ports></span><span class="sxs-lookup"><span data-stu-id="978ea-121"><xref:Microsoft.VisualBasic.Devices.Ports></span></span>   
 [<span data-ttu-id="978ea-122">Accès aux ports de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="978ea-122">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)

