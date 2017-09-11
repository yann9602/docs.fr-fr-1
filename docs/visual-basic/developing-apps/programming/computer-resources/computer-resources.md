---
title: "Accès aux ressources de l’ordinateur (Visual Basic)"
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
- computer resources
- My.Computer object, tasks
- computer resources, accessing
ms.assetid: 75b81c88-f7c0-46e0-95c8-0c006d2120f9
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
ms.openlocfilehash: ae9517d2c06c2583a90b2bb503094094bb6e938c
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="accessing-computer-resources-visual-basic"></a><span data-ttu-id="c80a1-102">Accès aux ressources de l’ordinateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c80a1-102">Accessing computer resources (Visual Basic)</span></span>

<span data-ttu-id="c80a1-103">L’objet `My.Computer` est l’un des trois objets centraux dans `My`, permettant d’accéder aux informations et aux fonctionnalités couramment utilisées.</span><span class="sxs-lookup"><span data-stu-id="c80a1-103">The `My.Computer` object is one of the three central objects in `My`, providing access to information and commonly used functionality.</span></span> <span data-ttu-id="c80a1-104">`My.Computer` fournit des méthodes, des propriétés et des événements pour l’accès à l’ordinateur sur lequel l’application s’exécute.</span><span class="sxs-lookup"><span data-stu-id="c80a1-104">`My.Computer` provides methods, properties, and events for accessing the computer on which the application is running.</span></span> <span data-ttu-id="c80a1-105">Il inclut les objets suivants :</span><span class="sxs-lookup"><span data-stu-id="c80a1-105">Its objects include:</span></span>  
  
-   <xref:Microsoft.VisualBasic.Devices.Audio>
-   <span data-ttu-id="c80a1-106">Presse-papiers (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span><span class="sxs-lookup"><span data-stu-id="c80a1-106">Clipboard (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span></span>
-   <xref:Microsoft.VisualBasic.Devices.Clock>
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem>
-   <xref:Microsoft.VisualBasic.Devices.ServerComputer.Info%2A>
-   <xref:Microsoft.VisualBasic.Devices.Keyboard>
-   <xref:Microsoft.VisualBasic.Devices.Mouse>
-   <xref:Microsoft.VisualBasic.Devices.Network>
-   <xref:Microsoft.VisualBasic.Devices.Ports>
-   <span data-ttu-id="c80a1-107">Registre (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span><span class="sxs-lookup"><span data-stu-id="c80a1-107">Registry (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="c80a1-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c80a1-108">In this section</span></span>

<span data-ttu-id="c80a1-109">[Lecture de sons](../../../../visual-basic/developing-apps/programming/computer-resources/playing-sounds.md) </span><span class="sxs-lookup"><span data-stu-id="c80a1-109">[Playing Sounds](../../../../visual-basic/developing-apps/programming/computer-resources/playing-sounds.md) </span></span>  
<span data-ttu-id="c80a1-110">Répertorie les tâches associées à `My.Computer.Audio`, telles que la lecture d’un son en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="c80a1-110">Lists tasks associated with `My.Computer.Audio`, such as playing a sound in the background.</span></span>

<span data-ttu-id="c80a1-111">[Stockage de données dans le Presse-papiers et lecture du Presse-papiers](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md) </span><span class="sxs-lookup"><span data-stu-id="c80a1-111">[Storing Data to and Reading from the Clipboard](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md) </span></span>  
<span data-ttu-id="c80a1-112">Répertorie les tâches associées à `My.Computer.Clipboard`, telles que la lecture ou l’écriture de données dans le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="c80a1-112">Lists tasks associated with `My.Computer.Clipboard`, such as reading data from or writing data to the Clipboard.</span></span>

<span data-ttu-id="c80a1-113">[Obtention d’informations sur l’ordinateur](../../../../visual-basic/developing-apps/programming/computer-resources/getting-information-about-the-computer.md) </span><span class="sxs-lookup"><span data-stu-id="c80a1-113">[Getting Information about the Computer](../../../../visual-basic/developing-apps/programming/computer-resources/getting-information-about-the-computer.md) </span></span>  
<span data-ttu-id="c80a1-114">Répertorie les tâches associées à `My.Computer.Info`, par exemple déterminer le nom complet ou les adresses IP d’un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c80a1-114">Lists tasks associated with `My.Computer.Info`, such as determining a computer's full name or IP addresses.</span></span>

<span data-ttu-id="c80a1-115">[Accès au clavier](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md) </span><span class="sxs-lookup"><span data-stu-id="c80a1-115">[Accessing the Keyboard](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md) </span></span>  
<span data-ttu-id="c80a1-116">Répertorie les tâches associées à `My.Computer.Keyboard`, par exemple déterminer si la touche VERR. MAJ est activée.</span><span class="sxs-lookup"><span data-stu-id="c80a1-116">Lists tasks associated with `My.Computer.Keyboard`, such as determining whether CAPS LOCK is on.</span></span>

<span data-ttu-id="c80a1-117">[Accès à la souris](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-mouse.md) </span><span class="sxs-lookup"><span data-stu-id="c80a1-117">[Accessing the Mouse](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-mouse.md) </span></span>  
<span data-ttu-id="c80a1-118">Répertorie les tâches associées à `My.Computer.Mouse`, par exemple déterminer si une souris est présente.</span><span class="sxs-lookup"><span data-stu-id="c80a1-118">Lists tasks associated with `My.Computer.Mouse`, such as determining whether a mouse is present.</span></span>

<span data-ttu-id="c80a1-119">[Exécution d’opérations de réseau](../../../../visual-basic/developing-apps/programming/computer-resources/performing-network-operations.md) </span><span class="sxs-lookup"><span data-stu-id="c80a1-119">[Performing Network Operations](../../../../visual-basic/developing-apps/programming/computer-resources/performing-network-operations.md) </span></span>  
<span data-ttu-id="c80a1-120">Répertorie les tâches associées à `My.Computer.Network`, telles que le chargement ou le téléchargement de fichiers.</span><span class="sxs-lookup"><span data-stu-id="c80a1-120">Lists tasks associated with `My.Computer.Network`, such as uploading or downloading files.</span></span>

<span data-ttu-id="c80a1-121">[Accès aux ports de l’ordinateur](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md) </span><span class="sxs-lookup"><span data-stu-id="c80a1-121">[Accessing the Computer's Ports](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md) </span></span>  
<span data-ttu-id="c80a1-122">Répertorie les tâches associées à `My.Computer.Ports`, telles que l’affichage des ports série disponibles ou l’envoi de chaînes aux ports série.</span><span class="sxs-lookup"><span data-stu-id="c80a1-122">Lists tasks associated with `My.Computer.Ports`, such as showing available serial ports or sending strings to serial ports.</span></span>

<span data-ttu-id="c80a1-123">[Lecture et écriture dans le Registre](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md) </span><span class="sxs-lookup"><span data-stu-id="c80a1-123">[Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md) </span></span>  
<span data-ttu-id="c80a1-124">Répertorie les tâches associées à `My.Computer.Registry`, telles que la lecture ou l’écriture de données dans les clés de Registre.</span><span class="sxs-lookup"><span data-stu-id="c80a1-124">Lists tasks associated with `My.Computer.Registry`, such as reading data from or writing data to registry keys.</span></span>

