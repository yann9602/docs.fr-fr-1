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
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a>Utilisation de manipulations et de l'inertie dans une application XNA
Cet article explique comment utiliser le traitement des manipulations et de l'inertie dans une application Microsoft XNA pour contrôler le déplacement de pièces de jeu. Avant de lire cet article, vous devez connaître les notions de la rubrique [Vue d’ensemble des manipulations et de l’inertie](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) et les concepts de base de la programmation XNA.  
  
 Pour effectuer les tâches décrites dans cet article, votre projet XNA doit référencer l’assembly <xref:System.Windows.Input.Manipulations> et [XNA Game Studio](http://msdn.microsoft.com/library/bb200104.aspx) ([télécharger](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) doit être installé sur votre ordinateur afin que votre projet puisse référencer les assemblys XNA.  
  
## <a name="overview-of-functionality"></a>Vue d'ensemble des fonctionnalités  
 Cet article montre comment créer une classe personnalisée représentant une pièce de jeu qui utilise le traitement des manipulations et de l'inertie. Cette classe vous permet de manipuler une pièce de jeu sur l'écran en la faisant glisser avec la souris, puis en la relâchant. Une fois la pièce relâchée, elle continue de se déplacer grâce au traitement de l'inertie, tout en ralentissant progressivement. Le déplacement est à la fois linéaire et angulaire.  
  
 ![Application de manipulations et d’inertie simple.](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")  
  
 De plus, une collection personnalisée est créée pour gérer plusieurs pièces de jeu. Elle permet de simplifier la gestion requise par la classe XNA Game.  
  
 [Création de la classe GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [Création de la classe GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [Création de la classe Game1](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [Listes complètes des codes](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Input.Manipulations>  
 [Vue d'ensemble des manipulations et de l'inertie](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)
