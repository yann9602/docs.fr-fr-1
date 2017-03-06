---
title: Notions de base du garbage collection
description: Notions de base du garbage collection
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 9d5fce64-95a4-4609-8eee-b0ac70078cdb
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 02b0311559071147b38182076f60918b7351cc63
ms.lasthandoff: 03/02/2017

---

# <a name="fundamentals-of-garbage-collection"></a>Notions de base du garbage collection

Dans le Common Language Runtime (CLR), le Garbage collector a un rôle de gestionnaire de mémoire automatique. Il fournit les avantages suivants :

* Il vous permet de développer votre application sans avoir à libérer de la mémoire. 

* Il alloue efficacement les objets sur le tas managé. 

* Il libère les objets qui ne sont plus utilisés, efface leur mémoire et garde la mémoire disponible pour les futures allocations. Les objets managés obtiennent automatiquement un contenu propre au démarrage, ce qui fait que leurs constructeurs n'ont pas à initialiser chaque champ de données.

* Il sécurise la mémoire en s'assurant qu'un objet ne peut pas utiliser le contenu d'un autre objet.


Cette rubrique décrit les concepts fondamentaux du garbage collection. Elle contient les sections suivantes :

* [Notions de base de la mémoire](#fundamentals-of-memory)

* [Conditions pour une opération garbage collection](#conditions-for-a-garbage-collection)

* [Tas managé](#the-managed-heap)

* [Générations](#generations)

* [Déroulement d’une opération garbage collection](#what-happens-during-a-garbage-collection)

* [Manipulation des ressources non managées](#manipulating-unmanaged-resources)

## <a name="fundamentals-of-memory"></a>Notions de base de la mémoire

La liste suivante résume les concepts importants de la mémoire CLR.

* Chaque processus possède son propre espace d'adressage virtuel séparé. Tous les processus sur le même ordinateur partagent la même mémoire physique et le fichier d'échange s'il en existe un.

* Par défaut, sur les ordinateurs 32 bits, chaque processus a un espace d'adressage virtuel en mode utilisateur de 2 Go.

* En tant que développeur d'applications, vous travaillez uniquement avec l'espace d'adressage virtuel et ne gérez jamais directement la mémoire physique. Le garbage collector alloue et libère la mémoire virtuelle pour vous sur le tas managé.

* La mémoire virtuelle peut être dans trois états : 

    * Libre. Il n'existe aucune référence au bloc de mémoire et celui-ci est disponible pour allocation.

    * Réservé. Le bloc de mémoire est disponible pour votre utilisation et ne peut pas être utilisé pour une autre demande d'allocation. Toutefois, vous ne pouvez pas stocker de données dans ce bloc de mémoire tant qu'il n'est pas validé. 

    * Validé. Le bloc de mémoire est assigné au stockage physique.

* L'espace d'adressage virtuel peut être fragmenté. Cela signifie qu'il existe des blocs libres, également appelés trous, dans l'espace d'adressage. Lorsqu'une allocation de mémoire virtuelle est demandée, le gestionnaire de mémoire virtuelle doit rechercher un bloc unique libre suffisamment grand pour satisfaire la demande d'allocation. Même si vous disposez de 2 Go d'espace libre, l'allocation qui requiert 2 Go échoue, sauf si tout cet espace est contenu dans un bloc d'adresse unique.

* Vous pouvez manquer de mémoire si vous manquez d'espace d'adressage virtuel à réserver ou d'espace physique à valider.

Votre fichier d'échange est utilisé, même si la sollicitation de la mémoire physique (c'est-à-dire, la demande de mémoire physique) est faible. La première fois que la sollicitation de la mémoire physique est élevée, le système d'exploitation doit libérer de la place dans la mémoire physique pour stocker des données et sauvegarde une partie des données qui sont dans la mémoire physique dans le fichier d'échange. Ces données ne sont pas paginées tant qu'elles ne sont pas nécessaires, il est donc possible de rencontrer la pagination dans les situations dans lesquelles la sollicitation de la mémoire physique est très faible.

## <a name="conditions-for-a-garbage-collection"></a>Conditions pour une opération garbage collection

Le garbage collection se produit lorsque l'une des conditions suivantes est vraie :

* Le système possède peu de mémoire physique.

* La mémoire utilisée par les objets alloués sur le tas managé dépasse un seuil acceptable. Ce seuil est continuellement ajusté à mesure que le processus s'exécute.

* La méthode [GC.Collect](xref:System.GC.Collect) est appelée. Dans presque tous les cas, vous n’avez pas à appeler cette méthode, car le garbage collector s’exécute continuellement. Cette méthode est principalement utilisée pour les situations uniques et les tests. 

## <a name="the-managed-heap"></a>Tas managé

Une fois que le garbage collector est initialisé par le CLR, il alloue un segment de mémoire pour stocker et gérer des objets. Cette mémoire est appelée tas managé, par opposition à un tas natif dans le système d'exploitation. 

Il existe un tas managé pour chaque processus managé. Tous les threads du processus allouent de la mémoire pour les objets sur le même tas.

> [!IMPORTANT]
> La taille des segments alloués par le garbage collector est spécifique à l'implémentation et susceptible de changer à tout moment, y compris les mises à jour périodiques. Votre application ne doit jamais faire d'hypothèses concernant une taille de segment particulière, ni dépendre de celle-ci. Elle ne doit pas non plus tenter de configurer la quantité de mémoire disponible pour les allocations de segments. 
 
Moins il y a d'objets alloués sur le tas, moins le garbage collector a à faire. Lorsque vous allouez des objets, n'utilisez pas de valeurs arrondies qui dépassent vos besoins, par exemple en allouant un tableau de 32 octets lorsque vous avez besoin de seulement 15 octets. 

Lorsqu'un garbage collection est déclenché, le garbage collector libère la mémoire occupée par les objets morts. Le processus de libération compacte les objets vivants afin qu'ils soient déplacés ensemble, et l'espace inutilisé est supprimé, ce qui entraîne la diminution du tas. Les objets alloués ensemble restent ainsi ensemble sur le tas managé, pour conserver leur emplacement.

Le déroulement (fréquence et durée) des garbage collection est le résultat du volume des allocations et de la quantité de mémoire restante sur le tas managé. 

Le tas peut être considéré comme l'accumulation de deux tas : le tas d'objets volumineux et le tas de petits objets. 

Le tas d'objets volumineux contient de très grands objets de 85 000 octets ou plus. Ces objets du tas d'objets volumineux sont généralement des tableaux. Il est rare qu'un objet d'instance soit extrêmement grand. 

## <a name="generations"></a>Générations

Le tas est organisé en générations. Il peut ainsi gérer des objets durables et éphémères. Le garbage collection consiste principalement en la récupération d'objets éphémères qui occupent généralement une petite partie du tas. Il existe trois générations d'objets sur le tas : 

* **Génération 0.** Il s'agit de la génération la plus jeune, qui contient des objets éphémères. Un exemple d'objet éphémère est une variable temporaire. Le garbage collection a le plus souvent lieu dans cette génération. 

  Les objets alloués récemment forment une nouvelle génération d'objets et sont implicitement des collections de génération 0, à moins qu'ils ne s'agissent de grands objets, auquel cas ils entrent dans le tas d'objets volumineux dans une collection de génération 2.

  La plupart des objets sont libérés pour l’opération garbage collection dans la génération 0 et ne survivent pas à la génération suivante. 

* **Génération 1.** Cette génération contient des objets éphémères et sert de tampon entre objets éphémères et objets durables. 

* **Génération 2.** Cette génération contient des objets durables. Un exemple d'objet durable est un objet dans une application serveur qui contient des données statiques qui sont vivantes pour la durée du processus.

Les opérations garbage collection se produisent sur des générations spécifiques, selon les conditions spécifiées. La collecte d'une génération signifie la collecte des objets de cette génération et de toutes ses générations plus jeunes. Les opérations garbage collection de génération 2 sont également appelées garbage collection complet, car elles libèrent tous les objets de toutes les générations (autrement dit, tous les objets du tas managé).

### <a name="survival-and-promotions"></a>Survie et promotions

Les objets qui ne sont pas libérés dans un garbage collection sont appelé survivants et sont promus à la génération suivante. Les objets qui survivent à un garbage collection de génération 0 sont promus à la génération 1, les objets qui survivent à un garbage collection de génération 1 sont promus à la génération 2 et les objets qui survivent à un garbage collection de génération 2 restent dans la génération 2.

Lorsque le garbage collector détecte que le taux de survie est élevé dans une génération, il augmente le seuil des allocations de cette génération. La collecte suivante récupère donc une taille substantielle de mémoire libérée. Le CLR équilibre continuellement deux priorités : ne pas permettre au jeu de travail d'une application de devenir trop grand et ne pas permettre pas au garbage collection d'être trop long.

### <a name="ephemeral-generations-and-segments"></a>Segments et générations éphémères

Étant donné que les objets des générations 0 et 1 sont éphémères, ces générations sont appelées générations éphémères. 

Les générations éphémères doivent être allouées dans le segment de mémoire appelé segment éphémère. Chaque nouveau segment acquis par le garbage collector devient le nouveau segment éphémère et contient les objets qui ont survécu à un garbage collection de génération 0. L'ancien segment éphémère devient le nouveau segment de génération 2. 


Le segment éphémère peut inclure des objets de la génération 2. Les objets de génération 2 peuvent utiliser plusieurs segments (autant que votre processus en requiert et que la mémoire en autorise). 

La quantité de mémoire libérée à partir d'un garbage collection éphémère est limitée à la taille du segment éphémère. La quantité de mémoire libérée est proportionnelle à l'espace occupé par les objets morts.

## <a name="what-happens-during-a-garbage-collection"></a>Déroulement d’une opération garbage collection

Une opération garbage collection présente les phases suivantes : 

* Une phase de marquage qui recherche et crée une liste de tous les objets actifs.

* Une phase de déplacement qui met à jour les références aux objets qui seront compactés. 

* Une phase de compactage qui libère l'espace occupé par les objets morts et compacte les objets survivants. La phase de compactage déplace les objets qui ont survécu à un garbage collection vers l'extrémité la plus ancienne du segment. 

Étant donné que les collections de génération 2 peuvent occuper plusieurs segments, les objets promus dans la génération 2 peuvent être déplacés dans un segment plus ancien. Les survivants des générations 1 et 2 peuvent être déplacés vers un autre segment, car ils sont promus à la génération 2. 

Normalement, le tas d'objets volumineux n'est pas compacté, car la copie d'objets volumineux implique une diminution des performances. Vous pouvez toutefois utiliser la propriété[GCSettings.LargeObjectHeapCompactionMode](xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode) pour compresser le tas d’objets volumineux à la demande. 

Le garbage collector utilise les informations suivantes pour déterminer si les objets sont vivants : 

* **Racines de pile.** Variables de pile fournies par le compilateur juste-à-temps (JIT) et l'explorateur de pile.

* **Handles de garbage collection.** Handles qui pointent vers les objets managés qui peuvent être alloués par le code utilisateur ou par le Common Language Runtime.

* **Données statiques.** Objets statiques des domaines d'application qui pourraient référencer d'autres objets. Chaque domaine d'application effectue le suivi de ses objets statiques.

Avant qu'une opération garbage collection ne démarre, tous les threads managés sont suspendus à l'exception du thread qui a déclenché l'opération.

L'illustration suivante montre un thread qui déclenche un garbage collection et entraîne l'interruption des autres threads.

![Lorsqu’un thread déclenche un garbage collection](./media/fundamentals/393001.png)

Thread qui déclenche un garbage collection

## <a name="manipulating-unmanaged-resources"></a>Manipulation des ressources non managées

Si vos objets managés référencent des objets non managés à l'aide de leurs handles de fichiers natifs, vous devez libérer explicitement les objets non managés, car le garbage collector effectue le suivi de la mémoire uniquement sur le tas managé.

Les utilisateurs de votre objet managé ne peuvent pas supprimer les ressources natives utilisées par l'objet. Pour effectuer le nettoyage, vous pouvez rendre votre objet managé finalisable. La finalisation est constituée des actions de nettoyage que vous exécutez lorsque l'objet n'est plus utilisé. Lorsque votre objet managé meurt, il effectue les actions de nettoyage spécifiées dans sa méthode de finaliseur.

Lorsqu'un objet finalisable est détecté comme étant mort, son finaliseur est placé dans une file d'attente afin que ses actions de nettoyage soient exécutées, mais l'objet lui-même est promu à la génération suivante. Par conséquent, vous devez attendre jusqu’au garbage collection suivant sur cette génération (qui n’est pas nécessairement le garbage collection suivant) pour déterminer si l’objet a été récupéré.

## <a name="see-also"></a>Voir aussi

[Garbage collection dans le .NET](gc.md)

