---
title: "Création de la classe Game1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47932ce3-2ba5-476f-a26b-3ddfd5226f27
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 1e4fd15013f10667b397e010fff56b7bc6a0f641
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-the-game1-class"></a><span data-ttu-id="19a1b-102">Création de la classe Game1</span><span class="sxs-lookup"><span data-stu-id="19a1b-102">Creating the Game1 Class</span></span>
<span data-ttu-id="19a1b-103">Comme dans tous les projets Microsoft XNA, la classe Game1 dérive de la classe [Microsoft.Xna.Framework.Game](http://msdn.microsoft.com/library/microsoft.xna.framework.game.aspx) qui fournit l’initialisation de base des périphériques graphiques, la logique de jeu et le code de rendu pour les jeux XNA.</span><span class="sxs-lookup"><span data-stu-id="19a1b-103">As with all Microsoft XNA projects, the Game1 class derives from the [Microsoft.Xna.Framework.Game](http://msdn.microsoft.com/library/microsoft.xna.framework.game.aspx) class, which provides basic graphics device initialization, game logic, and rendering code for XNA games.</span></span> <span data-ttu-id="19a1b-104">La classe Game1 est relativement simple dans la mesure où la majeure partie du travail est effectuée dans les classes GamePiece et GamePieceCollection.</span><span class="sxs-lookup"><span data-stu-id="19a1b-104">The Game1 class is fairly simple because most of the work in done in the GamePiece and GamePieceCollection classes.</span></span>  
  
## <a name="creating-the-code"></a><span data-ttu-id="19a1b-105">Création du code</span><span class="sxs-lookup"><span data-stu-id="19a1b-105">Creating the Code</span></span>  
 <span data-ttu-id="19a1b-106">Les membres privés de la classe se composent d’un objet **GamePieceCollection** pour contenir les pièces de jeu, d’un objet [GraphicsDeviceManager](http://msdn.microsoft.com/library/microsoft.xna.framework.graphicsdevicemanager.aspx) et d’un objet [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) pour le rendu des pièces de jeu.</span><span class="sxs-lookup"><span data-stu-id="19a1b-106">The private members for the class consist of a **GamePieceCollection** object to hold the game pieces, a [GraphicsDeviceManager](http://msdn.microsoft.com/library/microsoft.xna.framework.graphicsdevicemanager.aspx) object, and a [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) object used to render game pieces.</span></span>  
  
 [!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]  
  
 <span data-ttu-id="19a1b-107">Pendant l'initialisation du jeu, ces objets sont instanciés.</span><span class="sxs-lookup"><span data-stu-id="19a1b-107">During game initialization, these objects are instantiated.</span></span>  
  
 [!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]  
  
 <span data-ttu-id="19a1b-108">Quand la méthode [LoadContent](http://msdn.microsoft.com/library/microsoft.xna.framework.game.loadcontent.aspx) est appelée, les pièces de jeu sont créées et assignées à l’objet **GamePieceCollection**.</span><span class="sxs-lookup"><span data-stu-id="19a1b-108">When the [LoadContent](http://msdn.microsoft.com/library/microsoft.xna.framework.game.loadcontent.aspx) method is called, the game pieces are created and assigned to the **GamePieceCollection** object.</span></span> <span data-ttu-id="19a1b-109">Il existe deux types de pièces de jeu.</span><span class="sxs-lookup"><span data-stu-id="19a1b-109">There are two types of game pieces.</span></span> <span data-ttu-id="19a1b-110">Le facteur d'échelle pour les pièces est légèrement modifié pour créer des pièces plus petites et d'autres plus grandes.</span><span class="sxs-lookup"><span data-stu-id="19a1b-110">The scale factor for the pieces is changed slightly so that there are some smaller and some larger pieces.</span></span>  
  
 [!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]  
  
 <span data-ttu-id="19a1b-111">La méthode [Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) est appelée plusieurs fois par XNA Framework pendant l’exécution du jeu.</span><span class="sxs-lookup"><span data-stu-id="19a1b-111">The [Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) method is called repeatedly by the XNA Framework while the game is running.</span></span> <span data-ttu-id="19a1b-112">La méthode [Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) appelle les méthodes **ProcessInertia** et **UpdateFromMouse** dans la collection de pièces de jeu.</span><span class="sxs-lookup"><span data-stu-id="19a1b-112">The [Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) method calls the **ProcessInertia** and the **UpdateFromMouse** methods on the game piece collection.</span></span> <span data-ttu-id="19a1b-113">Ces méthodes sont décrites dans [Création de la classe GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).</span><span class="sxs-lookup"><span data-stu-id="19a1b-113">These methods are described in [Creating the GamePieceCollection Class](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).</span></span>  
  
 [!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]  
  
 <span data-ttu-id="19a1b-114">La méthode [Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) est également appelée plusieurs fois par XNA Framework pendant l’exécution du jeu.</span><span class="sxs-lookup"><span data-stu-id="19a1b-114">The [Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) method is also called repeatedly by the XNA Framework while the game is running.</span></span> <span data-ttu-id="19a1b-115">La méthode [Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) effectue le rendu des pièces de jeu en appelant la méthode **Draw** de l’objet **GamePieceCollection**.</span><span class="sxs-lookup"><span data-stu-id="19a1b-115">The [Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) method performs the rendering of game pieces by calling the **Draw** method of the **GamePieceCollection** object.</span></span> <span data-ttu-id="19a1b-116">Cette méthode est décrite dans [Création de la classe GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).</span><span class="sxs-lookup"><span data-stu-id="19a1b-116">This method is described in[Creating the GamePieceCollection Class](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).</span></span>  
  
 [!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]  
  
## <a name="see-also"></a><span data-ttu-id="19a1b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19a1b-117">See Also</span></span>  
 [<span data-ttu-id="19a1b-118">Manipulations et inertie</span><span class="sxs-lookup"><span data-stu-id="19a1b-118">Manipulations and Inertia</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [<span data-ttu-id="19a1b-119">Utilisation de manipulations et de l'inertie dans une application XNA</span><span class="sxs-lookup"><span data-stu-id="19a1b-119">Using Manipulations and Inertia in an XNA Application</span></span>](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [<span data-ttu-id="19a1b-120">Création de la classe GamePiece</span><span class="sxs-lookup"><span data-stu-id="19a1b-120">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [<span data-ttu-id="19a1b-121">Création de la classe GamePieceCollection</span><span class="sxs-lookup"><span data-stu-id="19a1b-121">Creating the GamePieceCollection Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [<span data-ttu-id="19a1b-122">Listes complètes des codes</span><span class="sxs-lookup"><span data-stu-id="19a1b-122">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)
