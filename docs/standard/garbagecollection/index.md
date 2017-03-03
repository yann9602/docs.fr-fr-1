---
title: Garbage Collection
description: Garbage Collection
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.devlang: dotnet
ms.assetid: db39a0f5-e363-490f-a7e6-adb9a6ff2a8c
translationtype: Human Translation
ms.sourcegitcommit: ffc0530b2263db0e073f351aac2d539de6701ead
ms.openlocfilehash: 4646a7e8c75315bb1a13bc5fddecd77888f6ae69
ms.lasthandoff: 01/18/2017

---

# <a name="garbage-collection"></a>Garbage collection

Le Garbage collection est une des fonctionnalités les plus importantes de la plateforme de code managé .NET. Le Garbage collector (GC) gère automatiquement l’allocation et la libération de la mémoire. Vous n’avez pas besoin d’allouer et de libérer de la mémoire ou de gérer la durée de vie des objets qui utilisent cette mémoire. Une allocation est effectuée chaque fois que vous créez un _nouvel_ objet ou qu’un type valeur est boxed. Les allocations sont généralement très rapides. Quand la mémoire est insuffisante pour allouer un objet, le Garbage collector doit collecter et supprimer la mémoire qui n’est plus référencée pour libérer de la mémoire pour de nouvelles allocations. Ce processus est appelé « garbage collection ».

Le Garbage collector a un rôle de gestionnaire de mémoire automatique. Il fournit les avantages suivants :

*   Il vous permet de développer votre application sans avoir à libérer de la mémoire.
*   Il alloue efficacement les objets sur le tas managé.
*   Il libère les objets qui ne sont plus utilisés, efface leur mémoire et garde la mémoire disponible pour les futures allocations. Les objets managés obtiennent automatiquement un contenu propre au démarrage, ce qui fait que leurs constructeurs n'ont pas à initialiser chaque champ de données.
*   Il sécurise la mémoire en s'assurant qu'un objet ne peut pas utiliser le contenu d'un autre objet.

Le Garbage collector .NET est générationnel et comprend 3 générations. Chaque génération possède son propre tas qu’elle utilise pour le stockage des objets alloués. Il existe un principe de base selon lequel la plupart des objets sont soit éphémères, soit durables. C’est dans la génération 0 que les objets sont d’abord alloués. Souvent, les objets ne vivent pas au-delà de la première génération, car ils ne sont plus utilisés (hors de portée) au moment où le garbage collection suivant se produit. La collection de la génération 0 s’effectue rapidement, car le tas qui est associé à cette dernière est petit. La génération 1 est véritablement un espace de la deuxième chance. Les objets éphémères mais qui survivent à la collection de génération 0 (souvent basée sur un minutage fortuit) accèdent à la génération 1\. Les collections de génération 1 sont également rapides, car le tas qui lui est associé est également petit. Les deux premiers tas restent petits, car les objets sont soit collectés, soit promus au tas de la génération suivante. C’est dans la génération 2 que se trouvent tous les objets durables. La taille du tas de génération 2 peut augmenter pour qu’il devienne très volumineux, car les objets qu’il contient peuvent survivre longtemps et il n’existe pas de tas de génération 3 pour promouvoir davantage les objets.

Le Garbage collector comporte un tas supplémentaire pour les objets volumineux, appelé « tas des objets volumineux » (LOH). Il est réservé aux objets qui ont une taille de 85 000 octets ou plus. Un tableau d’octets (Byte[]) comprenant 85 000 éléments est un exemple d’objet volumineux. Les objets volumineux ne sont pas alloués aux tas générationnels mais sont alloués directement au tas des objets volumineux.

Les collections de génération 2 et du tas des objets volumineux peuvent prendre un temps considérable pour les programmes dont l’exécution a été longue ou qui ont exploité de grandes quantités de données. Les programmes des serveurs volumineux sont connus pour avoir des sauts de dizaines de gigaoctets. Le Garbage collector utilise différentes techniques pour réduire le temps pendant lequel il bloque l’exécution du programme. La principale approche consiste à faire autant de tâches de garbage collection que possible sur un thread d’arrière-plan d’une manière qui n’interfère pas avec l’exécution du programme. Le Garbage collector expose également plusieurs façons pour les développeurs d’influencer son comportement, ce qui peut être très utile pour améliorer les performances.

## <a name="related-topics"></a>Rubriques connexes

Titre | Description
----- | ----------- 
[Gestion automatique de la mémoire et garbage collection](gc.md) | Présente les concepts de base de la gestion de la mémoire dans le .NET
[Notions de base du garbage collection](fundamentals.md) | Décrit le fonctionnement du garbage collection, l’allocation des objets sur le tas managé, ainsi que d’autres concepts principaux.
[Collections forcées](induced.md) | Décrit comment faire pour qu’un garbage collection se produise.
[Modes de latence](latency.md) | Décrit les modes qui déterminent le niveau d’intrusion du garbage collection.
[Références faibles](weak-references.md) | Décrit les fonctionnalités qui permettent au Garbage collector de collecter un objet tout en permettant à l’application d’accéder à cet objet.
 
## <a name="reference"></a>Référence

[System.GC](xref:System.GC)

[System.GCCollectionMode](xref:System.GCCollectionMode)

[System.Runtime.GCLatencyMode](xref:System.Runtime.GCLatencyMode)

[System.Runtime.GCSettings](xref:System.Runtime.GCSettings)

[GCSettings.LargeObjectHeapCompactionMode](xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode)

[Object.Finalize](xref:System.Object.Finalize)

[System.IDisposable](xref:System.IDisposable)

## <a name="see-also"></a>Voir aussi

[Nettoyage de ressources non managées](unmanaged.md)


