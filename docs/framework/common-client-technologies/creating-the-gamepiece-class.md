---
title: "Création de la classe GamePiece"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37a27a86-ac1c-47be-b477-cb4b819459d3
caps.latest.revision: 9
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7ac9884766812cd635b5a70c028cf15c19838511
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="creating-the-gamepiece-class"></a>Création de la classe GamePiece
La classe **GamePiece** encapsule toutes les fonctionnalités requises pour charger une image de pièce de jeu Microsoft XNA, suivre l’état de la souris par rapport à la pièce de jeu, capturer la souris, fournir une manipulation et un traitement de l’inertie, et permettre à la pièce de jeu de rebondir quand elle atteint les limites du port d’affichage.  
  
## <a name="private-members"></a>Membres privés  
 Au sommet de la classe **GamePiece**, plusieurs membres privés sont déclarés.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privatemembers)]  
  
## <a name="public-properties"></a>Propriétés publiques  
 Trois de ces membres privés sont exposés via des propriétés publiques. Les propriétés **Scale** et **PieceColor** permettent à l’application de spécifier, respectivement, l’échelle et la couleur de la pièce. La propriété **Bounds** est exposée pour permettre à une pièce d’utiliser les limites d’une autre pièce pour être rendue, par exemple quand une pièce doit se superposer à une autre. Le code suivant affiche la déclaration des propriétés publiques.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PublicProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_publicproperties)]  
  
## <a name="class-constructor"></a>Constructeur de classe  
 Le constructeur de la classe **GamePiece** accepte les paramètres suivants :  
  
-   Un type [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx). La référence passée ici est assignée au membre privé `spriteBatch` ; elle est utilisée pour accéder à la méthode [SpriteBatch.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.draw.aspx) quand la pièce de jeu est rendue. Par ailleurs, la propriété [GraphicsDevice](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.graphicsdevice.aspx) est utilisée pour créer l’objet [Texture](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.texture.aspx) associé à la pièce de jeu, mais aussi obtenir la taille du port d’affichage pour détecter quand la pièce de jeu rencontre une limite de fenêtre et la faire rebondir.  
  
-   Une chaîne qui spécifie le nom de fichier de l'image à utiliser pour la pièce de jeu.  
  
 Le constructeur crée également un objet <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> et un objet <xref:System.Windows.Input.Manipulations.InertiaProcessor2D>, et établit des gestionnaires d'événements pour leurs événements.  
  
 Le code suivant montre le constructeur pour la classe **GamePiece**.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Constructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_constructor)]  
  
## <a name="capturing-mouse-input"></a>Capture de l'entrée de la souris  
 La méthode **UpdateFromMouse** est chargée de détecter quand l’utilisateur appuie sur un bouton de la souris, tant que celle-ci se trouve dans les limites de la pièce de jeu, et quand l’utilisateur relâche le bouton de la souris.  
  
 Quand l'utilisateur appuie sur le bouton gauche de la souris (celle-ci se trouvant dans les limites de la pièce), cette méthode définit un indicateur pour signaler que cette pièce de jeu a capturé la souris, et commence le traitement de la manipulation.  
  
 Le traitement de la manipulation est démarré en créant un tableau d'objets <xref:System.Windows.Input.Manipulations.Manipulator2D> et en les passant à l'objet <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D>. Le processeur de manipulation évalue alors les manipulateurs (ici, un seul manipulateur) et déclenche des événements de manipulation.  
  
 Par ailleurs, le point où se produit le glissement est enregistré. Cette opération est utilisée ultérieurement lors de l'événement <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> pour ajuster les valeurs de translation de delta afin que la pièce de jeu s'aligne derrière le point de glissement.  
  
 Enfin, cette méthode retourne l'état de la capture de la souris. Cela permet à l’objet [GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) de gérer la capture quand il existe plusieurs pièces de jeu.  
  
 Le code suivant montre la méthode **UpdateFromMouse**.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_updatefrommouse)]  
  
## <a name="processing-manipulations"></a>Traitement des manipulations  
 Au début d'une manipulation, l'événement <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> est déclenché. Le gestionnaire de cet événement arrête le traitement de l’inertie, le cas échéant, et affecte à l’indicateur *processInertia* la valeur `false`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationStarted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationstarted)]  
  
 À mesure que les valeurs associées à la manipulation sont modifiées, l'événement <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> est déclenché. Le gestionnaire de cet événement utilise les valeurs delta passées aux arguments de l’événement pour modifier les valeurs de rotation et de position de la pièce de jeu.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationdelta)]  
  
 Quand tous les manipulateurs (ici, un seul manipulateur) associés à une manipulation sont supprimés, le processeur de manipulation déclenche l'événement <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed>. Le gestionnaire de cet événement commence le traitement de l’inertie en attribuant les rapidités initiales indiquées par les arguments de l’événement à celles du processeur d’inertie et affecte à l’indicateur *processInertia* la valeur `true`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationcompleted)]  
  
## <a name="processing-inertia"></a>Traitement de l'inertie  
 À mesure que le traitement de l'inertie extrapole de nouvelles valeurs pour les rapidités angulaires et linéaires, les coordonnées de position (translation) et la rotation, l'événement <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> est déclenché. Le gestionnaire de cet événement utilise les valeurs delta passées aux arguments de l'événement pour modifier les valeurs de rotation et de position de la pièce de jeu.  
  
 Si la pièce de jeu sort des limites du port d'affichage en raison des nouvelles coordonnées, la rapidité du traitement de l'inertie est inversée. Ainsi, la pièce de jeu rebondit sur la limite du port d'affichage qu'elle a rencontrée.  
  
 Vous ne pouvez pas modifier les propriétés d'un objet <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> pendant qu'il exécute l'extrapolation. Par conséquent, lors de l'inversion de la rapidité X ou Y, le gestionnaire d'événements arrête d'abord l'inertie en appelant la méthode <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Complete%2A>. Il assigne ensuite les nouvelles valeurs de rapidités initiales en tant que valeurs de rapidités actuelles (ajustées pour un comportement d’éponge) et affecte à l’indicateur *processInertia* la valeur `true`.  
  
 Le code suivant montre le gestionnaire d'événements pour l'événement <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta>.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiadelta)]  
  
 Une fois le traitement de l'inertie terminé, le processeur d'inertie déclenche l'événement <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Completed>. Le gestionnaire de cet événement affecte à l’indicateur *processInertia* la valeur `false`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiacompleted)]  
  
 La logique présentée jusqu'à présent n'entraîne en aucun cas une extrapolation de l'inertie. Cette opération est accomplie dans la méthode **ProcessInertia**. Cette méthode, qui est appelée plusieurs fois à partir de la boucle de mise à jour du jeu (méthode [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx)), vérifie si l’indicateur *processInertia* a la valeur `true` et, le cas échéant, appelle la méthode <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Process%2A>. L'appel de cette méthode entraîne l'extrapolation et déclenche l'événement <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta>.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_ProcessInertia](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_processinertia)]  
  
 En réalité, la pièce de jeu n'est rendue qu'au moment de l'appel de l'une des surcharges de la méthode Draw. La première surcharge de cette méthode est appelée plusieurs fois à partir de la boucle de dessin du jeu (méthode [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx)). Elle assure le rendu de la pièce de jeu avec les facteurs actuels de position, de rotation et d'échelle.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Draw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_draw)]  
  
## <a name="additional-properties"></a>Autres propriétés  
 Trois propriétés privées sont utilisées par la classe **GamePiece**.  
  
1.  **Timestamp** : obtient une valeur d’horodatage utilisée par les processeurs d’inertie et de manipulation.  
  
2.  **X** : obtient ou définit la coordonnée X de la pièce de jeu. Lors de la configuration, règle les limites utilisées pour les tests de résultats et l'emplacement du pivot du processeur de manipulation.  
  
3.  **Y** : obtient ou définit la coordonnée Y de la pièce de jeu. Lors de la configuration, règle les limites utilisées pour les tests de résultats et l'emplacement du pivot du processeur de manipulation.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privateproperties)]  
  
## <a name="see-also"></a>Voir aussi  
 [Manipulations et inertie](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)   
 [Utilisation de manipulations et de l’inertie dans une application XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)   
 [Création de la classe GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)   
 [Création de la classe Game1](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)

