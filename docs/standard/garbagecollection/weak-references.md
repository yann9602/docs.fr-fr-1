---
title: "Références faibles"
description: "Références faibles"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/19/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 22319f2f-0008-4ace-815e-545892a0512a
translationtype: Human Translation
ms.sourcegitcommit: 213ce098bcc2b5e31c55e759d895254d5ca33caa
ms.openlocfilehash: a966f430c00f07d48f2210d64f03d6805f4e3097

---

# <a name="weak-references"></a>Références faibles

Le Garbage collector ne peut pas collecter un objet actuellement utilisé par une application, tandis que le code de l’application peut accéder à cet objet. On dit de l’application qu’elle a une référence forte à l’objet. 

Une référence faible permet au Garbage collector de collecter l’objet tout en permettant à l’application d’y accéder. Une référence faible est valide uniquement pour une période indéterminée jusqu’à ce que l’objet soit collecté quand il n’existe aucune référence forte. Quand vous utilisez une référence faible, l’application peut toujours obtenir une référence forte à l’objet, ce qui l’empêche d’être collecté. Toutefois, il existe toujours un risque que le Garbage collector accède à l’objet avant qu’une référence forte soit rétablie.

Les références faibles sont utiles pour les objets qui utilisent beaucoup de mémoire, mais peuvent être recréées facilement si elles sont récupérées par le garbage collection. 

Supposons que l’arborescence présente à l’utilisateur un choix hiérarchique d’options complexe. Si les données sous-jacentes sont volumineuses, la conservation de l’arborescence en mémoire est inefficace quand l’utilisateur est impliqué dans un autre élément de l’application. 

Quand l’utilisateur passe à une autre partie de l’application, vous pouvez utiliser la classe [WeakReference](xref:System.WeakReference) ou [WeakReference&lt;T&gt;](xref:System.WeakReference%601) pour créer une référence faible à l’arborescence et détruire toutes les références fortes. Quand l’utilisateur revient à l’arborescence, l’application tente d’obtenir une référence forte à l’arborescence et, en cas de réussite, évite de reconstruire l’arborescence.

Pour établir une référence faible à un objet, vous créez un [WeakReference](xref:System.WeakReference) à l’aide de l’instance de l’objet à suivre. Vous affectez ensuite cet objet à la propriété [Target](xref:System.WeakReference.Target) et vous définissez la référence d’origine à l’objet sur null. 

## <a name="short-and-long-weak-references"></a>Références faibles courtes et longues

Vous pouvez créer une référence faible courte ou une référence faible longue : 

* Courte

  La cible d’une référence faible courte devient `null` quand l’objet est récupéré par le garbage collection. La référence faible est elle-même un objet managé et fait l’objet d’un garbage collection comme tout autre objet managé. Une référence faible courte est le constructeur par défaut [WeakReference](xref:System.WeakReference). 

* Longue

  Une référence faible longue est conservée après l’appel de la méthode [Finalize](xref:System.Object.Finalize). Cela permet à l’objet d’être recréé, mais l’état de l’objet reste imprévisible. Pour utiliser une référence longue, spécifiez `true` dans le constructeur [WeakReference](xref:System.WeakReference). 

  Si le type de l’objet ne dispose pas d’une méthode [Finalize](xref:System.Object.Finalize), la fonctionnalité de la référence faible courte s’applique et la référence faible est valide uniquement jusqu’à la collecte de la cible, ce qui peut se produire à tout moment après l’exécution du finaliseur.

Pour établir une référence forte et réutiliser l’objet, effectuez un cast de la propriété [Target](xref:System.WeakReference.Target) d’un [WeakReference](xref:System.WeakReference) vers le type de l’objet. Si la propriété [Target](xref:System.WeakReference.Target) retourne la valeur `null`, l’objet a été collecté ; sinon, vous pouvez continuer à utiliser l’objet, car l’application a récupéré une référence forte à celui-ci.

## <a name="guidelines-for-using-weak-references"></a>Instructions d’utilisation de références faibles

Utilisez des références faibles longues uniquement quand cela est nécessaire, car l’état de l’objet est imprévisible après la finalisation. 

Évitez d’utiliser des références faibles aux petits objets, car le pointeur lui-même peut être de la même taille ou d’une taille supérieure. 

Évitez d’utiliser les références faibles comme solution automatique aux problèmes de gestion de la mémoire. Développez plutôt une stratégie de mise en cache efficace pour gérer les objets de votre application. 

## <a name="see-also"></a>Voir aussi

[Garbage collection dans .NET](index.md)



<!--HONumber=Nov16_HO3-->


