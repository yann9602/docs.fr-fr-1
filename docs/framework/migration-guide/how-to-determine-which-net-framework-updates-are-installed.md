---
title: "Comment : déterminer les mises à jour .NET Framework installées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ba734dd3a9585b52b96cb2d27743da6190961126
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-determine-which-net-framework-updates-are-installed"></a><span data-ttu-id="cfd10-102">Comment : déterminer les mises à jour .NET Framework installées</span><span class="sxs-lookup"><span data-stu-id="cfd10-102">How to: Determine Which .NET Framework Updates Are Installed</span></span>
<span data-ttu-id="cfd10-103">Les mises à jour installées pour chaque version du .NET Framework installée sur un ordinateur sont répertoriées dans le Registre Windows.</span><span class="sxs-lookup"><span data-stu-id="cfd10-103">The installed updates for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="cfd10-104">Vous pouvez utiliser l'Éditeur du Registre (regedit.exe) pour afficher ces informations.</span><span class="sxs-lookup"><span data-stu-id="cfd10-104">You can use the Registry Editor (regedit.exe) to view this information.</span></span>  
  
 <span data-ttu-id="cfd10-105">Dans l'Éditeur du Registre, les versions du .NET Framework et les mises à jour installées pour chaque version sont stockées dans des sous-clés distinctes.</span><span class="sxs-lookup"><span data-stu-id="cfd10-105">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="cfd10-106">Pour plus d'informations sur la détection des numéros des versions installées, voir [Comment : déterminer les versions .NET Framework installées](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="cfd10-106">For information about detecting the installed version numbers, see [How to: Determine Which .NET Framework Versions Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span> <span data-ttu-id="cfd10-107">Pour plus d’informations sur l’installation du .NET Framework, consultez [Installer le .NET Framework pour les développeurs](../../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="cfd10-107">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
### <a name="to-find-installed-updates"></a><span data-ttu-id="cfd10-108">Pour trouver les mises à jour installées</span><span class="sxs-lookup"><span data-stu-id="cfd10-108">To find installed updates</span></span>  
  
1.  <span data-ttu-id="cfd10-109">Ouvrez le programme **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="cfd10-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="cfd10-110">Dans Windows 8 et les versions ultérieures, ouvrez l'écran d'accueil et tapez le nom.</span><span class="sxs-lookup"><span data-stu-id="cfd10-110">In Windows 8 and higher open the Start screen and type the name.</span></span> <span data-ttu-id="cfd10-111">Dans les versions antérieures de Windows, dans le menu **Démarrer**, choisissez **Exécuter** puis, dans la zone **Ouvrir**, entrez **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="cfd10-111">In earlier versions of Windows, on the **Start** menu, choose **Run** and then, in the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="cfd10-112">Vous devez disposer d'informations d'identification d'administration pour exécuter regedit.exe.</span><span class="sxs-lookup"><span data-stu-id="cfd10-112">You must have administrative credentials to run regedit.exe.</span></span>  
  
2.  <span data-ttu-id="cfd10-113">Dans l'Éditeur du Registre, ouvrez la sous-clé suivante :</span><span class="sxs-lookup"><span data-stu-id="cfd10-113">In the Registry Editor, open the following subkey:</span></span>  
  
     <span data-ttu-id="cfd10-114">HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates</span><span class="sxs-lookup"><span data-stu-id="cfd10-114">HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates</span></span>  
  
     <span data-ttu-id="cfd10-115">Les mises à jour installées sont répertoriées sous les sous-clés qui identifient la version du .NET Framework auquel elles s'appliquent.</span><span class="sxs-lookup"><span data-stu-id="cfd10-115">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="cfd10-116">Chaque mise à jour est identifiée par un numéro de Base de connaissances (KB).</span><span class="sxs-lookup"><span data-stu-id="cfd10-116">Each update is identified by a Knowledge Base (KB) number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfd10-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="cfd10-117">Example</span></span>  
 <span data-ttu-id="cfd10-118">Le code suivant détermine par programmation les mises à jour du .NET Framework installées sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="cfd10-118">The following code programmatically determines the .NET Framework updates that are installed on a computer.</span></span> <span data-ttu-id="cfd10-119">Vous devez disposer d'informations d'identification d'administration pour exécuter cet exemple.</span><span class="sxs-lookup"><span data-stu-id="cfd10-119">You must have administrative credentials to run this example.</span></span>  
  
 [!code-csharp[ListUpdates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs#1)]
 [!code-vb[ListUpdates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb#1)]  
  
 <span data-ttu-id="cfd10-120">Cet exemple produit un résultat semblable au suivant :</span><span class="sxs-lookup"><span data-stu-id="cfd10-120">The example produces output that's similar to the following:</span></span>  
  
```  
Microsoft .NET Framework 3.5 SP1  
  KB953595  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB953595)  
  SP1  
    KB2657424  Security Update for Microsoft .NET Framework 3.5 SP1 (KB2657424)  
    KB958484  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB958484)  
    KB963707  Update for Microsoft .NET Framework 3.5 SP1 (KB963707)  
Microsoft .NET Framework 4 Client Profile  
  KB2160841  Security Update for Microsoft .NET Framework 4 Client Profile (KB2160841)  
  KB2446708  Security Update for Microsoft .NET Framework 4 Client Profile (KB2446708)  
  KB2468871  Update for Microsoft .NET Framework 4 Client Profile (KB2468871)  
  KB2478663  Security Update for Microsoft .NET Framework 4 Client Profile (KB2478663)  
  KB2518870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2518870)  
  KB2533523  Update for Microsoft .NET Framework 4 Client Profile (KB2533523)  
  KB2539636  Security Update for Microsoft .NET Framework 4 Client Profile (KB2539636)  
  KB2572078  Security Update for Microsoft .NET Framework 4 Client Profile (KB2572078)  
  KB2633870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2633870)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Client Profile (KB2656351)  
Microsoft .NET Framework 4 Extended  
  KB2416472  Security Update for Microsoft .NET Framework 4 Extended (KB2416472)  
  KB2468871  Update for Microsoft .NET Framework 4 Extended (KB2468871)  
  KB2487367  Security Update for Microsoft .NET Framework 4 Extended (KB2487367)  
  KB2533523  Update for Microsoft .NET Framework 4 Extended (KB2533523)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Extended (KB2656351)  
```  
  
## <a name="see-also"></a><span data-ttu-id="cfd10-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cfd10-121">See also</span></span>

<span data-ttu-id="cfd10-122">[Guide pratique pour déterminer les versions .NET Framework installées](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) </span><span class="sxs-lookup"><span data-stu-id="cfd10-122">[How to: Determine Which .NET Framework Versions Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) </span></span>  
<span data-ttu-id="cfd10-123">[Installation du .NET Framework](../../../docs/framework/install/guide-for-developers.md) </span><span class="sxs-lookup"><span data-stu-id="cfd10-123">[Installing the .NET Framework](../../../docs/framework/install/guide-for-developers.md) </span></span>  
[<span data-ttu-id="cfd10-124">Versions et dépendances</span><span class="sxs-lookup"><span data-stu-id="cfd10-124">Versions and Dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)
