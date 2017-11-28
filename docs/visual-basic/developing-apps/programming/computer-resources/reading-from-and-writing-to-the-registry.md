---
title: "Lecture et écriture dans le Registre (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: db564b428d585829b220674271f4636bfcc68562
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a><span data-ttu-id="977d2-102">Lecture et écriture dans le Registre (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="977d2-102">Reading from and Writing to the Registry (Visual Basic)</span></span>
<span data-ttu-id="977d2-103">Cette rubrique décrit les rubriques de concepts et de tâches associées au Registre.</span><span class="sxs-lookup"><span data-stu-id="977d2-103">This topic describes task and conceptual topics that are associated with the registry.</span></span>  
  
 <span data-ttu-id="977d2-104">Lorsque vous programmez en [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], vous pouvez choisir d’accéder au Registre via les fonctions fournies par [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ou les classes registry du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="977d2-104">When programming in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], you can choose to access the registry by means of either the functions provided by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] or the registry classes of the .NET Framework.</span></span> <span data-ttu-id="977d2-105">Le Registre contient des informations provenant du système d’exploitation et des applications hébergées sur la machine.</span><span class="sxs-lookup"><span data-stu-id="977d2-105">The registry hosts information from the operating system as well as information from applications hosted on the machine.</span></span> <span data-ttu-id="977d2-106">L’utilisation du Registre peut compromettre la sécurité en accordant un accès inapproprié à des ressources système ou à des informations protégées.</span><span class="sxs-lookup"><span data-stu-id="977d2-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="977d2-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="977d2-107">In This Section</span></span>  
 [<span data-ttu-id="977d2-108">Guide pratique : créer une clé de Registre et définir sa valeur</span><span class="sxs-lookup"><span data-stu-id="977d2-108">How to: Create a Registry Key and Set Its Value</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 <span data-ttu-id="977d2-109">Décrit comment utiliser les méthodes `CreateSubKey` et `SetValue` de l’objet `My.Computer.Registry` pour créer une clé de Registre et définir sa valeur.</span><span class="sxs-lookup"><span data-stu-id="977d2-109">Describes how to use the `CreateSubKey` and `SetValue` methods of the `My.Computer.Registry` object to create a registry key and set its value.</span></span>  
  
 [<span data-ttu-id="977d2-110">Guide pratique : lire une valeur à partir d’une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="977d2-110">How to: Read a Value from a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 <span data-ttu-id="977d2-111">Décrit comment utiliser la méthode `GetValue` de l’objet `My.Computer.Registry` pour lire une valeur à partir d’une clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="977d2-111">Describes how to use the `GetValue` method of the `My.Computer.Registry` object to read a value from a registry key.</span></span>  
  
 [<span data-ttu-id="977d2-112">Guide pratique : supprimer une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="977d2-112">How to: Delete a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 <span data-ttu-id="977d2-113">Décrit comment utiliser la méthode `DeleteSubKey` de la propriété `My.Computer.Registry.CurrentUser` pour supprimer une clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="977d2-113">Describes how to use the `DeleteSubKey` method of the `My.Computer.Registry.CurrentUser` property to delete a registry key.</span></span>  
  
 [<span data-ttu-id="977d2-114">Lecture et écriture dans le Registre à l’aide de l’espace de noms Microsoft.Win32</span><span class="sxs-lookup"><span data-stu-id="977d2-114">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 <span data-ttu-id="977d2-115">Décrit comment utiliser les classes `Registry` et `RegistryKey` du [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pour accéder au Registre.</span><span class="sxs-lookup"><span data-stu-id="977d2-115">Describes how to use the `Registry` and `RegistryKey` classes of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] to access the registry.</span></span>  
  
 [<span data-ttu-id="977d2-116">Sécurité et Registre</span><span class="sxs-lookup"><span data-stu-id="977d2-116">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 <span data-ttu-id="977d2-117">Décrit les problèmes de sécurité impliquant le Registre.</span><span class="sxs-lookup"><span data-stu-id="977d2-117">Discusses security issues involving the registry.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="977d2-118">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="977d2-118">Related Sections</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <span data-ttu-id="977d2-119">Répertorie et décrit les membres de l’objet `My.Computer.Registry`.</span><span class="sxs-lookup"><span data-stu-id="977d2-119">Lists and explains members of the `My.Computer.Registry` object.</span></span>  
  
 <xref:Microsoft.Win32.Registry>  
 <span data-ttu-id="977d2-120">Présente une vue d’ensemble de la classe `Registry`, ainsi que des liens vers des clés et des membres individuels.</span><span class="sxs-lookup"><span data-stu-id="977d2-120">Presents an overview of the `Registry` class, along with links to individual keys and members.</span></span>
