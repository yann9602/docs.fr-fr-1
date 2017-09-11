---
title: Utilisation de manipulations et de l'inertie dans une application XNA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
caps.latest.revision: 7
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7d623a8c2276811ae443a4d745faffeeb79ffc6f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a><span data-ttu-id="b7fec-102">Utilisation de manipulations et de l'inertie dans une application XNA</span><span class="sxs-lookup"><span data-stu-id="b7fec-102">Using Manipulations and Inertia in an XNA Application</span></span>
<span data-ttu-id="b7fec-103">Cet article explique comment utiliser le traitement des manipulations et de l'inertie dans une application Microsoft XNA pour contrôler le déplacement de pièces de jeu.</span><span class="sxs-lookup"><span data-stu-id="b7fec-103">This article describes how you can use manipulations and inertia processing in a Microsoft XNA application to control the movement of game pieces.</span></span> <span data-ttu-id="b7fec-104">Avant de lire cet article, vous devez connaître les notions de la rubrique [Vue d’ensemble des manipulations et de l’inertie](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) et les concepts de base de la programmation XNA.</span><span class="sxs-lookup"><span data-stu-id="b7fec-104">Before you read this article, you should be familiar with the [Manipulations and Inertia Overview](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) topic, and be familiar with basic XNA programming concepts.</span></span>  
  
 <span data-ttu-id="b7fec-105">Pour effectuer les tâches décrites dans cet article, votre projet XNA doit référencer l’assembly <xref:System.Windows.Input.Manipulations> et [XNA Game Studio](http://msdn.microsoft.com/library/bb200104.aspx) ([télécharger](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) doit être installé sur votre ordinateur afin que votre projet puisse référencer les assemblys XNA.</span><span class="sxs-lookup"><span data-stu-id="b7fec-105">To perform the tasks described in this article, your XNA project must reference the <xref:System.Windows.Input.Manipulations> assembly, and you must have [XNA Game Studio](http://msdn.microsoft.com/library/bb200104.aspx) ([download](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) installed on your computer so that your project can reference the XNA assemblies.</span></span>  
  
## <a name="overview-of-functionality"></a><span data-ttu-id="b7fec-106">Vue d'ensemble des fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="b7fec-106">Overview of Functionality</span></span>  
 <span data-ttu-id="b7fec-107">Cet article montre comment créer une classe personnalisée représentant une pièce de jeu qui utilise le traitement des manipulations et de l'inertie.</span><span class="sxs-lookup"><span data-stu-id="b7fec-107">This article shows you how to create a custom class that represents a game piece that uses manipulation and inertia processing.</span></span> <span data-ttu-id="b7fec-108">Cette classe vous permet de manipuler une pièce de jeu sur l'écran en la faisant glisser avec la souris, puis en la relâchant.</span><span class="sxs-lookup"><span data-stu-id="b7fec-108">This class enables you to manipulate a game piece across the screen by dragging it with the mouse, and then releasing it.</span></span> <span data-ttu-id="b7fec-109">Une fois la pièce relâchée, elle continue de se déplacer grâce au traitement de l'inertie, tout en ralentissant progressivement.</span><span class="sxs-lookup"><span data-stu-id="b7fec-109">Once released, inertia processing keeps the game piece moving as it gradually slows down.</span></span> <span data-ttu-id="b7fec-110">Le déplacement est à la fois linéaire et angulaire.</span><span class="sxs-lookup"><span data-stu-id="b7fec-110">Movement is both linear and angular.</span></span>  
  
 <span data-ttu-id="b7fec-111">![Application de manipulations et d’inertie simple.](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span><span class="sxs-lookup"><span data-stu-id="b7fec-111">![A simple manipulations and inertia application.](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span></span>  
  
 <span data-ttu-id="b7fec-112">De plus, une collection personnalisée est créée pour gérer plusieurs pièces de jeu.</span><span class="sxs-lookup"><span data-stu-id="b7fec-112">In addition, a custom collection is created that manages multiple game pieces.</span></span> <span data-ttu-id="b7fec-113">Elle permet de simplifier la gestion requise par la classe XNA Game.</span><span class="sxs-lookup"><span data-stu-id="b7fec-113">This simplifies the handling that is required from the XNA Game class.</span></span>  
  
 [<span data-ttu-id="b7fec-114">Création de la classe GamePiece</span><span class="sxs-lookup"><span data-stu-id="b7fec-114">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [<span data-ttu-id="b7fec-115">Création de la classe GamePieceCollection</span><span class="sxs-lookup"><span data-stu-id="b7fec-115">Creating the GamePieceCollection Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [<span data-ttu-id="b7fec-116">Création de la classe Game1</span><span class="sxs-lookup"><span data-stu-id="b7fec-116">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [<span data-ttu-id="b7fec-117">Listes complètes des codes</span><span class="sxs-lookup"><span data-stu-id="b7fec-117">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a><span data-ttu-id="b7fec-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7fec-118">See Also</span></span>  
 <span data-ttu-id="b7fec-119"><xref:System.Windows.Input.Manipulations></span><span class="sxs-lookup"><span data-stu-id="b7fec-119"><xref:System.Windows.Input.Manipulations></span></span>   
 [<span data-ttu-id="b7fec-120">Vue d'ensemble des manipulations et de l'inertie</span><span class="sxs-lookup"><span data-stu-id="b7fec-120">Manipulations and Inertia Overview</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)

