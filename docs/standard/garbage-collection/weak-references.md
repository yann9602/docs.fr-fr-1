---
title: "Références faibles"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 906c23caa7065486bb094ad2475ed9e7e24b3d9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="weak-references"></a>Références faibles
Le Garbage collector ne peut pas collecter un objet actuellement utilisé par une application, tandis que le code de l’application peut accéder à cet objet. On dit de l’application qu’elle a une référence forte à l’objet.  
  
 Une référence faible permet au Garbage collector de collecter l’objet tout en permettant à l’application d’y accéder. Une référence faible est valide uniquement pour une période indéterminée jusqu’à ce que l’objet soit collecté quand il n’existe aucune référence forte. Quand vous utilisez une référence faible, l’application peut toujours obtenir une référence forte à l’objet, ce qui l’empêche d’être collecté. Toutefois, il existe toujours un risque que le Garbage collector accède à l’objet avant qu’une référence forte soit rétablie.  
  
 Les références faibles sont utiles pour les objets qui utilisent beaucoup de mémoire, mais peuvent être recréées facilement si elles sont récupérées par le garbage collection.  
  
 Supposez qu’une arborescence dans une application Windows Forms affiche un choix hiérarchique complex d’options à l’utilisateur. Si les données sous-jacentes sont volumineuses, la conservation de l’arborescence en mémoire est inefficace quand l’utilisateur est impliqué dans un autre élément de l’application.  
  
 Lorsque l’utilisateur passe à une autre partie de l’application, vous pouvez utiliser la <xref:System.WeakReference> classe pour créer une référence faible à l’arborescence et la destruction de toutes les références fortes. Quand l’utilisateur revient à l’arborescence, l’application tente d’obtenir une référence forte à l’arborescence et, en cas de réussite, évite de reconstruire l’arborescence.  
  
 Pour établir une référence faible à un objet, vous créez un <xref:System.WeakReference> à l’aide de l’instance de l’objet à suivre. Vous définissez ensuite la <xref:System.WeakReference.Target%2A> à cet objet et le jeu d’origine font référence à l’objet de propriété `null`. Pour obtenir un exemple de code, consultez <xref:System.WeakReference> dans la bibliothèque de classes.  
  
## <a name="short-and-long-weak-references"></a>Références faibles courtes et longues  
 Vous pouvez créer une référence faible courte ou une référence faible longue :  
  
-   Courte  
  
     La cible d’une référence faible courte devient `null` quand l’objet est récupéré par le garbage collection. La référence faible est elle-même un objet managé et fait l’objet d’un garbage collection comme tout autre objet managé.  Une référence faible courte est le constructeur par défaut <xref:System.WeakReference>.  
  
-   Long  
  
     Une référence faible longue est conservée après l’objet <xref:System.Object.Finalize%2A> méthode a été appelée. Cela permet à l’objet d’être recréé, mais l’état de l’objet reste imprévisible. Pour utiliser une référence longue, spécifiez `true` dans le <xref:System.WeakReference> constructeur.  
  
     Si le type d’objet n’a pas un <xref:System.Object.Finalize%2A> (méthode), la référence faible courte fonctionnalité s’applique et la référence faible est valide uniquement jusqu'à ce que la cible est collectée, qui peut se produire à tout moment après le finaliseur n’est exécuté.  
  
 Pour établir une référence forte et utiliser à nouveau l’objet, effectuez un cast du <xref:System.WeakReference.Target%2A> propriété d’un <xref:System.WeakReference> pour le type de l’objet. Si le <xref:System.WeakReference.Target%2A> propriété renvoie `null`, l’objet a été collecté ; sinon, vous pouvez continuer à utiliser l’objet, car l’application a récupéré une référence forte à celui-ci.  
  
## <a name="guidelines-for-using-weak-references"></a>Instructions d’utilisation de références faibles  
 Utilisez des références faibles longues uniquement quand cela est nécessaire, car l’état de l’objet est imprévisible après la finalisation.  
  
 Évitez d’utiliser des références faibles aux petits objets, car le pointeur lui-même peut être de la même taille ou d’une taille supérieure.  
  
 Évitez d’utiliser les références faibles comme solution automatique aux problèmes de gestion de la mémoire. Développez plutôt une stratégie de mise en cache efficace pour gérer les objets de votre application.  
  
## <a name="see-also"></a>Voir aussi  
 [Nettoyage de la mémoire](../../../docs/standard/garbage-collection/index.md)
