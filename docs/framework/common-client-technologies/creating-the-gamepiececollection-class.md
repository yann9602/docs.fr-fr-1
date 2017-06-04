---
title: "Creating the GamePieceCollection Class | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e4b037ee-1201-4a55-b198-0d6532ed6f35
caps.latest.revision: 8
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 8
---
# Creating the GamePieceCollection Class
La classe **GamePieceCollection** dérive de la classe générique List et contient des méthodes permettant de gérer plus facilement plusieurs objets **GamePiece**.  
  
## Création du code  
 Le constructeur de la classe **GamePieceCollection** initialise le membre privé *capturedIndex*.  Ce champ est utilisé pour identifier la pièce de jeu qui contrôle actuellement la capture de la souris.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]  
  
 Les méthodes **ProcessInertia** et **Draw** simplifient le code requis dans les méthodes [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) et [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) du jeu en énumérant toutes les pièces de jeu dans la collection et en appelant la méthode correspondante sur chaque objet **GamePiece**.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]  
  
 La méthode **UpdateFromMouse** est également appelée pendant la mise à jour du jeu.  Elle permet à une pièce de jeu de capturer la souris en vérifiant d'abord si la capture actuelle \(le cas échéant\) est encore utilisée.  Dans ce cas, aucune autre pièce n'est autorisée à vérifier la capture.  
  
 Si aucune pièce n'a actuellement la capture, la méthode **UpdateFromMouse** énumère chaque pièce de jeu de la dernière à la première et vérifie si cette pièce signale une capture de la souris.  Dans ce cas, cette pièce devient la pièce actuellement capturée, et aucun traitement supplémentaire n'est effectué.  La méthode **UpdateFromMouse** vérifie d'abord le dernier élément dans la collection pour que, si deux pièces se chevauchent, la capture revienne à celle dont l'ordre de plan est le plus élevé.  L'ordre de plan n'est ni explicite ni modifiable ; il dépend simplement de l'ordre dans lequel les pièces de jeu sont ajoutées à la collection.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]  
  
## Voir aussi  
 [Manipulations and Inertia](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)   
 [Using Manipulations and Inertia in an XNA Application](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)   
 [Creating the GamePiece Class](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)   
 [Creating the Game1 Class](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)   
 [Full Code Listings](../../../docs/framework/common-client-technologies/full-code-listings.md)