---
title: Utilisation de manipulations et de l'inertie dans une application XNA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f7452a6001742bc9e0456ccb6339f13596a2ab72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a><span data-ttu-id="f817a-102">Utilisation de manipulations et de l'inertie dans une application XNA</span><span class="sxs-lookup"><span data-stu-id="f817a-102">Using Manipulations and Inertia in an XNA Application</span></span>
<span data-ttu-id="f817a-103">Cet article explique comment utiliser le traitement des manipulations et de l'inertie dans une application Microsoft XNA pour contrôler le déplacement de pièces de jeu.</span><span class="sxs-lookup"><span data-stu-id="f817a-103">This article describes how you can use manipulations and inertia processing in a Microsoft XNA application to control the movement of game pieces.</span></span> <span data-ttu-id="f817a-104">Avant de lire cet article, vous devez connaître les notions de la rubrique [Vue d’ensemble des manipulations et de l’inertie](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) et les concepts de base de la programmation XNA.</span><span class="sxs-lookup"><span data-stu-id="f817a-104">Before you read this article, you should be familiar with the [Manipulations and Inertia Overview](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) topic, and be familiar with basic XNA programming concepts.</span></span>  
  
 <span data-ttu-id="f817a-105">Pour effectuer les tâches décrites dans cet article, votre projet XNA doit référencer l’assembly <xref:System.Windows.Input.Manipulations> et [XNA Game Studio](http://msdn.microsoft.com/library/bb200104.aspx) ([télécharger](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) doit être installé sur votre ordinateur afin que votre projet puisse référencer les assemblys XNA.</span><span class="sxs-lookup"><span data-stu-id="f817a-105">To perform the tasks described in this article, your XNA project must reference the <xref:System.Windows.Input.Manipulations> assembly, and you must have [XNA Game Studio](http://msdn.microsoft.com/library/bb200104.aspx) ([download](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) installed on your computer so that your project can reference the XNA assemblies.</span></span>  
  
## <a name="overview-of-functionality"></a><span data-ttu-id="f817a-106">Vue d'ensemble des fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="f817a-106">Overview of Functionality</span></span>  
 <span data-ttu-id="f817a-107">Cet article montre comment créer une classe personnalisée représentant une pièce de jeu qui utilise le traitement des manipulations et de l'inertie.</span><span class="sxs-lookup"><span data-stu-id="f817a-107">This article shows you how to create a custom class that represents a game piece that uses manipulation and inertia processing.</span></span> <span data-ttu-id="f817a-108">Cette classe vous permet de manipuler une pièce de jeu sur l'écran en la faisant glisser avec la souris, puis en la relâchant.</span><span class="sxs-lookup"><span data-stu-id="f817a-108">This class enables you to manipulate a game piece across the screen by dragging it with the mouse, and then releasing it.</span></span> <span data-ttu-id="f817a-109">Une fois la pièce relâchée, elle continue de se déplacer grâce au traitement de l'inertie, tout en ralentissant progressivement.</span><span class="sxs-lookup"><span data-stu-id="f817a-109">Once released, inertia processing keeps the game piece moving as it gradually slows down.</span></span> <span data-ttu-id="f817a-110">Le déplacement est à la fois linéaire et angulaire.</span><span class="sxs-lookup"><span data-stu-id="f817a-110">Movement is both linear and angular.</span></span>  
  
 <span data-ttu-id="f817a-111">![Application de manipulations et d’inertie simple.](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span><span class="sxs-lookup"><span data-stu-id="f817a-111">![A simple manipulations and inertia application.](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span></span>  
  
 <span data-ttu-id="f817a-112">De plus, une collection personnalisée est créée pour gérer plusieurs pièces de jeu.</span><span class="sxs-lookup"><span data-stu-id="f817a-112">In addition, a custom collection is created that manages multiple game pieces.</span></span> <span data-ttu-id="f817a-113">Elle permet de simplifier la gestion requise par la classe XNA Game.</span><span class="sxs-lookup"><span data-stu-id="f817a-113">This simplifies the handling that is required from the XNA Game class.</span></span>  
  
 [<span data-ttu-id="f817a-114">Création de la classe GamePiece</span><span class="sxs-lookup"><span data-stu-id="f817a-114">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [<span data-ttu-id="f817a-115">Création de la classe GamePieceCollection</span><span class="sxs-lookup"><span data-stu-id="f817a-115">Creating the GamePieceCollection Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [<span data-ttu-id="f817a-116">Création de la classe Game1</span><span class="sxs-lookup"><span data-stu-id="f817a-116">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [<span data-ttu-id="f817a-117">Listes complètes des codes</span><span class="sxs-lookup"><span data-stu-id="f817a-117">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a><span data-ttu-id="f817a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f817a-118">See Also</span></span>  
 <xref:System.Windows.Input.Manipulations>  
 [<span data-ttu-id="f817a-119">Vue d'ensemble des manipulations et de l'inertie</span><span class="sxs-lookup"><span data-stu-id="f817a-119">Manipulations and Inertia Overview</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)
