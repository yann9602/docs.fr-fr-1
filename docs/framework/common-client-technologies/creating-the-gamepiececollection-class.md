---
title: "Création de la classe GamePieceCollection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4b037ee-1201-4a55-b198-0d6532ed6f35
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: b8b53e5890aaebbad2f0a5f0e058182193b11622
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-the-gamepiececollection-class"></a><span data-ttu-id="724f3-102">Création de la classe GamePieceCollection</span><span class="sxs-lookup"><span data-stu-id="724f3-102">Creating the GamePieceCollection Class</span></span>
<span data-ttu-id="724f3-103">La classe **GamePieceCollection** dérive de la classe générique List et contient des méthodes permettant de gérer plus facilement plusieurs objets **GamePiece**.</span><span class="sxs-lookup"><span data-stu-id="724f3-103">The **GamePieceCollection** class derives from the generic List class, and introduces methods to more easily manage multiple **GamePiece** objects.</span></span>  
  
## <a name="creating-the-code"></a><span data-ttu-id="724f3-104">Création du code</span><span class="sxs-lookup"><span data-stu-id="724f3-104">Creating the Code</span></span>  
 <span data-ttu-id="724f3-105">Le constructeur de la classe **GamePieceCollection** initialise le membre privé *capturedIndex*.</span><span class="sxs-lookup"><span data-stu-id="724f3-105">The constructor of the **GamePieceCollection** class initializes the private member *capturedIndex*.</span></span> <span data-ttu-id="724f3-106">Ce champ est utilisé pour identifier la pièce de jeu qui contrôle actuellement la capture de la souris.</span><span class="sxs-lookup"><span data-stu-id="724f3-106">This field is used to track which of the game pieces currently has the mouse capture.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]  
  
 <span data-ttu-id="724f3-107">Les méthodes **ProcessInertia** et **Draw** simplifient le code requis dans les méthodes [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) et [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) du jeu en énumérant toutes les pièces de jeu dans la collection et en appelant la méthode correspondante sur chaque objet **GamePiece**.</span><span class="sxs-lookup"><span data-stu-id="724f3-107">The **ProcessInertia** and the **Draw** methods simplify the code needed in the game [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) and [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) methods by enumerating all of the game pieces in the collection and calling the respective method on each **GamePiece** object.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]  
  
 <span data-ttu-id="724f3-108">La méthode **UpdateFromMouse** est également appelée pendant la mise à jour du jeu.</span><span class="sxs-lookup"><span data-stu-id="724f3-108">The **UpdateFromMouse** method is also called during game update.</span></span> <span data-ttu-id="724f3-109">Elle permet à une pièce de jeu de capturer la souris en vérifiant d'abord si la capture actuelle (le cas échéant) est encore utilisée.</span><span class="sxs-lookup"><span data-stu-id="724f3-109">It enables only one game piece to have the mouse capture by first checking to see if the current capture (if any) is still in effect.</span></span> <span data-ttu-id="724f3-110">Dans ce cas, aucune autre pièce n'est autorisée à vérifier la capture.</span><span class="sxs-lookup"><span data-stu-id="724f3-110">If so, no other piece is allowed to check for capture.</span></span>  
  
 <span data-ttu-id="724f3-111">Si aucune pièce n’a actuellement la capture, la méthode **UpdateFromMouse** énumère chaque pièce de jeu de la dernière à la première et vérifie si cette pièce signale une capture de la souris.</span><span class="sxs-lookup"><span data-stu-id="724f3-111">If no piece currently has the capture, the **UpdateFromMouse** method enumerates each game piece from last to first, and checks to see if that piece reports a mouse capture.</span></span> <span data-ttu-id="724f3-112">Dans ce cas, cette pièce devient la pièce actuellement capturée, et aucun traitement supplémentaire n'est effectué.</span><span class="sxs-lookup"><span data-stu-id="724f3-112">If so, that piece becomes the current captured piece, and no further processing takes place.</span></span> <span data-ttu-id="724f3-113">La méthode **UpdateFromMouse** vérifie d’abord le dernier élément dans la collection pour que, si deux pièces se chevauchent, la capture revienne à celle dont l’ordre de plan est le plus élevé.</span><span class="sxs-lookup"><span data-stu-id="724f3-113">The **UpdateFromMouse** method checks the last item in the collection first so that if two pieces are overlapped, the one with the higher Z-order will obtain the capture.</span></span> <span data-ttu-id="724f3-114">L’ordre de plan n’est ni explicite ni modifiable ; il dépend simplement de l’ordre dans lequel les pièces de jeu sont ajoutées à la collection.</span><span class="sxs-lookup"><span data-stu-id="724f3-114">Z-order is not explicit nor changeable; it is governed simply by the order in which game pieces are added to the collection.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]  
  
## <a name="see-also"></a><span data-ttu-id="724f3-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="724f3-115">See Also</span></span>  
 [<span data-ttu-id="724f3-116">Manipulations et inertie</span><span class="sxs-lookup"><span data-stu-id="724f3-116">Manipulations and Inertia</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [<span data-ttu-id="724f3-117">Utilisation de manipulations et de l'inertie dans une application XNA</span><span class="sxs-lookup"><span data-stu-id="724f3-117">Using Manipulations and Inertia in an XNA Application</span></span>](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [<span data-ttu-id="724f3-118">Création de la classe GamePiece</span><span class="sxs-lookup"><span data-stu-id="724f3-118">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [<span data-ttu-id="724f3-119">Création de la classe Game1</span><span class="sxs-lookup"><span data-stu-id="724f3-119">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
 [<span data-ttu-id="724f3-120">Listes complètes des codes</span><span class="sxs-lookup"><span data-stu-id="724f3-120">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)
