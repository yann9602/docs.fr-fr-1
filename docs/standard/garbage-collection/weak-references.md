---
title: "Weak References | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "weak references, short"
  - "weak references, using"
  - "weak references, long"
  - "garbage collection, weak references"
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Weak References
Le garbage collector ne peut pas collecter un objet utilisé par une application lorsque le code de l'application peut accéder à cet objet.  L'application est réputée contenir une référence forte à l'objet.  
  
 Une référence faible autorise le garbage collector à collecter l'objet tout en permettant à l'application d'accéder à l'objet.  Une référence faible est valide uniquement pour une période indéterminée, jusqu'à ce que l'objet soit collecté lorsqu'il n'existe aucune référence forte.  Lorsque vous utilisez une référence faible, l'application peut encore obtenir une référence forte à l'objet, ce qui empêche ce dernier d'être collecté.  Toutefois, il existe toujours un risque que le garbage collector accède à l'objet avant qu'une référence forte soit rétablie.  
  
 Les références faibles sont utiles pour les objets qui utilisent beaucoup de mémoire, mais peuvent être recréées facilement si elles sont récupérées par le garbage collection.  
  
 Supposons que l'arborescence d'une application Windows Forms présente à l'utilisateur un choix hiérarchique d'options complexe.  Si les données sous\-jacentes sont volumineuses, la conservation de l'arborescence en mémoire est inefficace lorsque l'utilisateur est concerné par un autre élément de l'application.  
  
 Lorsque l'utilisateur passe à une autre partie de l'application, vous pouvez utiliser la classe <xref:System.WeakReference> pour créer une référence faible à l'arborescence et détruire toutes les références fortes.  Lorsque l'utilisateur revient à l'arborescence, l'application tente d'obtenir une référence forte à l'arborescence et, en cas de réussite, évite de reconstruire l'arborescence.  
  
 Pour établir une référence faible à un objet, vous créez une <xref:System.WeakReference> à l'aide de l'instance de l'objet à suivre.  Vous affectez ensuite la propriété <xref:System.WeakReference.Target%2A> à cet objet et la valeur de référence `null` à l'objet.  Pour obtenir un exemple de code, consultez <xref:System.WeakReference> dans la bibliothèque de classes.  
  
## Références faibles courtes et longues  
 Vous pouvez créer une référence faible courte ou une référence faible longue :  
  
-   Short  
  
     La cible d'une référence faible courte devient `null` lorsque l'objet est récupéré par le garbage collection.  La référence faible est elle\-même un objet managé et fait l'objet d'un garbage collection comme tout autre objet managé.  Le constructeur par défaut de <xref:System.WeakReference> est une référence faible courte.  
  
-   Long  
  
     Une référence faible longue est conservée après l'appel de la méthode <xref:System.Object.Finalize%2A> de l'objet.  Cela permet à l'objet d'être recréé, mais l'état de l'objet reste imprévisible.  Pour utiliser une référence longue, spécifiez `true` dans le constructeur <xref:System.WeakReference>.  
  
     Si le type de l'objet ne dispose pas d'une méthode <xref:System.Object.Finalize%2A>, la fonctionnalité de la référence faible courte s'applique et la référence faible est valide uniquement jusqu'à la collecte de la cible, ce qui peut se produire à tout moment après l'exécution du finaliseur.  
  
 Pour établir une référence forte et utiliser à nouveau l'objet, effectuez un cast de la propriété <xref:System.WeakReference.Target%2A> d'une <xref:System.WeakReference> en ce type d'objet.  Si la propriété <xref:System.WeakReference.Target%2A> retourne la valeur `null`, l'objet a été collecté ; sinon, vous pouvez continuer à utiliser l'objet, car l'application a récupéré une référence forte à cet objet.  
  
## Indications sur l'utilisation de références faibles  
 Utilisez des références faibles longues uniquement lorsque cela est nécessaire, car l'état de l'objet est imprévisible après la finalisation.  
  
 Évitez d'utiliser des références faibles aux petits objets, car le pointeur lui\-même peut être de la même taille ou d'une taille supérieure.  
  
 Évitez d'utiliser les références faibles comme solution automatique aux problèmes de gestion de mémoire.  Développez plutôt une stratégie de mise en cache efficace pour gérer les objets de votre application.  
  
## Voir aussi  
 [Garbage Collection](../../../docs/standard/garbage-collection/index.md)