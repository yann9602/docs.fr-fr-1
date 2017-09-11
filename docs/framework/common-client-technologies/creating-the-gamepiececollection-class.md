---
title: "Création de la classe GamePieceCollection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4b037ee-1201-4a55-b198-0d6532ed6f35
caps.latest.revision: 8
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b74702d71113c3a9dac654971e7d02f97016218b
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="creating-the-gamepiececollection-class"></a><span data-ttu-id="4047f-102">Création de la classe GamePieceCollection</span><span class="sxs-lookup"><span data-stu-id="4047f-102">Creating the GamePieceCollection Class</span></span>
<span data-ttu-id="4047f-103">La classe **GamePieceCollection** dérive de la classe générique List et contient des méthodes permettant de gérer plus facilement plusieurs objets **GamePiece**.</span><span class="sxs-lookup"><span data-stu-id="4047f-103">The **GamePieceCollection** class derives from the generic List class, and introduces methods to more easily manage multiple **GamePiece** objects.</span></span>  
  
## <a name="creating-the-code"></a><span data-ttu-id="4047f-104">Création du code</span><span class="sxs-lookup"><span data-stu-id="4047f-104">Creating the Code</span></span>  
 <span data-ttu-id="4047f-105">Le constructeur de la classe **GamePieceCollection** initialise le membre privé *capturedIndex*.</span><span class="sxs-lookup"><span data-stu-id="4047f-105">The constructor of the **GamePieceCollection** class initializes the private member *capturedIndex*.</span></span> <span data-ttu-id="4047f-106">Ce champ est utilisé pour identifier la pièce de jeu qui contrôle actuellement la capture de la souris.</span><span class="sxs-lookup"><span data-stu-id="4047f-106">This field is used to track which of the game pieces currently has the mouse capture.</span></span>  
  
 <span data-ttu-id="4047f-107">[!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]</span><span class="sxs-lookup"><span data-stu-id="4047f-107">[!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]</span></span>  
  
 <span data-ttu-id="4047f-108">Les méthodes **ProcessInertia** et **Draw** simplifient le code requis dans les méthodes [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) et [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) du jeu en énumérant toutes les pièces de jeu dans la collection et en appelant la méthode correspondante sur chaque objet **GamePiece**.</span><span class="sxs-lookup"><span data-stu-id="4047f-108">The **ProcessInertia** and the **Draw** methods simplify the code needed in the game [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) and [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) methods by enumerating all of the game pieces in the collection and calling the respective method on each **GamePiece** object.</span></span>  
  
 <span data-ttu-id="4047f-109">[!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]</span><span class="sxs-lookup"><span data-stu-id="4047f-109">[!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]</span></span>  
  
 <span data-ttu-id="4047f-110">La méthode **UpdateFromMouse** est également appelée pendant la mise à jour du jeu.</span><span class="sxs-lookup"><span data-stu-id="4047f-110">The **UpdateFromMouse** method is also called during game update.</span></span> <span data-ttu-id="4047f-111">Elle permet à une pièce de jeu de capturer la souris en vérifiant d'abord si la capture actuelle (le cas échéant) est encore utilisée.</span><span class="sxs-lookup"><span data-stu-id="4047f-111">It enables only one game piece to have the mouse capture by first checking to see if the current capture (if any) is still in effect.</span></span> <span data-ttu-id="4047f-112">Dans ce cas, aucune autre pièce n'est autorisée à vérifier la capture.</span><span class="sxs-lookup"><span data-stu-id="4047f-112">If so, no other piece is allowed to check for capture.</span></span>  
  
 <span data-ttu-id="4047f-113">Si aucune pièce n’a actuellement la capture, la méthode **UpdateFromMouse** énumère chaque pièce de jeu de la dernière à la première et vérifie si cette pièce signale une capture de la souris.</span><span class="sxs-lookup"><span data-stu-id="4047f-113">If no piece currently has the capture, the **UpdateFromMouse** method enumerates each game piece from last to first, and checks to see if that piece reports a mouse capture.</span></span> <span data-ttu-id="4047f-114">Dans ce cas, cette pièce devient la pièce actuellement capturée, et aucun traitement supplémentaire n'est effectué.</span><span class="sxs-lookup"><span data-stu-id="4047f-114">If so, that piece becomes the current captured piece, and no further processing takes place.</span></span> <span data-ttu-id="4047f-115">La méthode **UpdateFromMouse** vérifie d’abord le dernier élément dans la collection pour que, si deux pièces se chevauchent, la capture revienne à celle dont l’ordre de plan est le plus élevé.</span><span class="sxs-lookup"><span data-stu-id="4047f-115">The **UpdateFromMouse** method checks the last item in the collection first so that if two pieces are overlapped, the one with the higher Z-order will obtain the capture.</span></span> <span data-ttu-id="4047f-116">L’ordre de plan n’est ni explicite ni modifiable ; il dépend simplement de l’ordre dans lequel les pièces de jeu sont ajoutées à la collection.</span><span class="sxs-lookup"><span data-stu-id="4047f-116">Z-order is not explicit nor changeable; it is governed simply by the order in which game pieces are added to the collection.</span></span>  
  
 <span data-ttu-id="4047f-117">[!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]</span><span class="sxs-lookup"><span data-stu-id="4047f-117">[!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4047f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4047f-118">See Also</span></span>  
 <span data-ttu-id="4047f-119">[Manipulations et inertie](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md) </span><span class="sxs-lookup"><span data-stu-id="4047f-119">[Manipulations and Inertia](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md) </span></span>  
 <span data-ttu-id="4047f-120">[Utilisation de manipulations et de l’inertie dans une application XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md) </span><span class="sxs-lookup"><span data-stu-id="4047f-120">[Using Manipulations and Inertia in an XNA Application](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md) </span></span>  
 <span data-ttu-id="4047f-121">[Création de la classe GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md) </span><span class="sxs-lookup"><span data-stu-id="4047f-121">[Creating the GamePiece Class](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md) </span></span>  
 <span data-ttu-id="4047f-122">[Création de la classe Game1](../../../docs/framework/common-client-technologies/creating-the-game1-class.md) </span><span class="sxs-lookup"><span data-stu-id="4047f-122">[Creating the Game1 Class](../../../docs/framework/common-client-technologies/creating-the-game1-class.md) </span></span>  
 [<span data-ttu-id="4047f-123">Listes complètes des codes</span><span class="sxs-lookup"><span data-stu-id="4047f-123">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)

