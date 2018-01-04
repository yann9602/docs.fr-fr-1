---
title: "Instanciation d’un objet DateTimeOffset"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
- DateTimeOffset structure, converting to DateTime
- DateTimeOffset structure, instantiating
ms.assetid: 9648375f-d368-4373-a976-3332ece00c0a
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 39095d3534de746008fd4710ffdb69db64c8cc86
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="instantiating-a-datetimeoffset-object"></a>Instanciation d'un objet DateTimeOffset

Le <xref:System.DateTimeOffset> structure offre plusieurs façons de créer de nouveaux <xref:System.DateTimeOffset> valeurs. Bon nombre d'entre elles correspondent directement aux méthodes d’instanciation de nouvelles <xref:System.DateTime> valeurs, avec des améliorations qui vous permettent de spécifier la valeur de date et heure du décalage par rapport au temps universel coordonné (UTC). En particulier, vous pouvez instancier un <xref:System.DateTimeOffset> valeur comme suit :

* En utilisant une date et heure de littéral.

* En appelant un <xref:System.DateTimeOffset> constructeur.

* En convertissant implicitement une valeur à <xref:System.DateTimeOffset> valeur.

* En analysant la représentation sous forme de chaîne d’une date et d’une heure.

Cette rubrique fournit des exemples de code et de détail supérieurs qui illustrent ces méthodes d’instanciation de nouvelles <xref:System.DateTimeOffset> valeurs.

## <a name="date-and-time-literals"></a>Littéraux de date et d’heure

Pour les langages qui prennent en charge, une des méthodes plus courantes pour instancier un <xref:System.DateTime> valeur consiste à fournir la date et l’heure sous la forme d’une valeur littérale codée en dur. Par exemple, le code Visual Basic suivant crée un <xref:System.DateTime> objet dont la valeur est le 1er janvier 2008 à 10 h 00.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset>les valeurs peuvent également être initialisées à l’aide de littéraux de date et d’heure lors de l’utilisation des langages qui prennent en charge <xref:System.DateTime> littéraux. Par exemple, le code Visual Basic suivant crée un <xref:System.DateTimeOffset> objet.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

Comme le montre la sortie de console, le <xref:System.DateTimeOffset> valeur créée de cette façon est assignée le décalage de fuseau horaire local. Cela signifie qu’un <xref:System.DateTimeOffset> valeur affectée à l’aide d’un littéral de caractère n’identifie pas un point unique de temps si le code est exécuté sur des ordinateurs différents.

## <a name="datetimeoffset-constructors"></a>Constructeurs DateTimeOffset

Le <xref:System.DateTimeOffset> type définit six constructeurs. Quatre d'entre elles correspondent directement aux <xref:System.DateTime> constructeurs, avec un paramètre supplémentaire de type <xref:System.TimeSpan> qui définit la date et l’offset d’heure à l’heure UTC. Vous permettent de définir un <xref:System.DateTimeOffset> valeur basée sur la valeur de sa date individuel et les composants heure. Par exemple, le code suivant utilise ces quatre constructeurs pour instancier <xref:System.DateTimeOffset> objets avec des valeurs identiques de 7/1/2008 12:05 AM + 01:00.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

Notez que, lorsque la valeur de la <xref:System.DateTimeOffset> objet instancié à l’aide un <xref:System.Globalization.PersianCalendar> objet en tant qu’un des arguments à son constructeur est affichée dans la console, elle est exprimée comme une date du calendrier grégorien plutôt que le calendrier persan. Pour obtenir une date à l’aide du calendrier persan, consultez l’exemple dans le <xref:System.Globalization.PersianCalendar> rubrique.

Les deux autres constructeurs créent un <xref:System.DateTimeOffset> de l’objet d’un <xref:System.DateTime> valeur. Le premier des deux possède un paramètre unique, le <xref:System.DateTime> valeur à convertir en un <xref:System.DateTimeOffset> valeur. Le décalage de la <xref:System.DateTimeOffset> valeur dépend de la <xref:System.DateTime.Kind%2A> propriété de paramètre du constructeur unique. Si sa valeur est <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, le décalage est défini comme égal à <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Sinon, son décalage est défini comme égal à celui du fuseau horaire local. L’exemple suivant illustre l’utilisation de ce constructeur pour instancier <xref:System.DateTimeOffset> objets qui représentent l’heure UTC et le fuseau horaire local :

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> Appel de la surcharge de la <xref:System.DateTimeOffset> constructeur ayant un seul <xref:System.DateTime> paramètre équivaut à effectuer une conversion implicite d’un <xref:System.DateTime> valeur un <xref:System.DateTimeOffset> valeur.

Le deuxième constructeur crée un <xref:System.DateTimeOffset> à partir de l’objet un <xref:System.DateTime> valeur possède deux paramètres : le <xref:System.DateTime> valeur à convertir et un <xref:System.TimeSpan> valeur représentant la date et l’heure de l’offset UTC. Cette valeur de décalage doit correspondre à la <xref:System.DateTime.Kind%2A> propriété de paramètre du constructeur premier ou un <xref:System.ArgumentException> est levée. Si le <xref:System.DateTime.Kind%2A> propriété du premier paramètre est <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, la valeur du deuxième paramètre doit être <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Si le <xref:System.DateTime.Kind%2A> propriété du premier paramètre est <xref:System.DateTimeKind.Local?displayProperty=nameWithType>, la valeur du deuxième paramètre doit être le décalage de fuseau horaire du système local. Si le <xref:System.DateTime.Kind%2A> propriété du premier paramètre est <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, le décalage peut être toute valeur valide. Le code suivant montre comment appeler ce constructeur pour convertir <xref:System.DateTime> à <xref:System.DateTimeOffset> valeurs.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>Conversion de type implicite

Le <xref:System.DateTimeOffset> type prend en charge une conversion de type implicite : d’un <xref:System.DateTime> valeur un <xref:System.DateTimeOffset> valeur. (Une conversion de type implicite est une conversion d’un type vers un autre qui ne nécessite pas de cast explicite (en C#) ni de conversion (en Visual Basic), et qui ne perd pas d’informations. Elle permet d’utiliser un code similaire au suivant.)

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

Le décalage de la <xref:System.DateTimeOffset> valeur dépend de la <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> valeur de propriété. Si sa valeur est <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, le décalage est défini comme égal à <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Si sa valeur est soit <xref:System.DateTimeKind.Local?displayProperty=nameWithType> ou <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, le décalage est égale à celle du fuseau horaire local.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>L’analyse de la représentation sous forme de chaîne de date et heure

Le <xref:System.DateTimeOffset> type prend en charge les quatre méthodes qui vous permettent de convertir la représentation sous forme de chaîne d’une date et d’heure dans un <xref:System.DateTimeOffset> valeur :

* <xref:System.DateTimeOffset.Parse%2A>, qui essaie de convertir la représentation sous forme de chaîne d’une date et l’heure à un <xref:System.DateTimeOffset> valeur et lève une exception si la conversion échoue.

* <xref:System.DateTimeOffset.TryParse%2A>, qui essaie de convertir la représentation sous forme de chaîne d’une date et l’heure à un <xref:System.DateTimeOffset> valeur et retourne `false` si la conversion échoue.

* <xref:System.DateTimeOffset.ParseExact%2A>, qui essaie de convertir la représentation sous forme de chaîne d’une date et une heure dans un format spécifié pour un <xref:System.DateTimeOffset> valeur. La méthode lève une exception si la conversion échoue.

* <xref:System.DateTimeOffset.TryParseExact%2A>, qui essaie de convertir la représentation sous forme de chaîne d’une date et une heure dans un format spécifié pour un <xref:System.DateTimeOffset> valeur. La méthode retourne `false` si la conversion échoue.

L’exemple suivant illustre des appels à chacune de ces méthodes de conversion de chaîne de quatre pour instancier un <xref:System.DateTimeOffset> valeur.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>Voir aussi

[Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
