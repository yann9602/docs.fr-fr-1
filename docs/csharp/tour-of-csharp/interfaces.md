---
title: "Interfaces C# - Visite guidée du langage C# | Microsoft Docs"
description: "Les interfaces définissent des contrats implémentés par les types en C#"
keywords: ".NET, csharp, interfaces, héritage multiple, polymorphisme"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: 6c18de7a4aa86a321b65b4ce65e07c48ca1dbc24
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---

<a id="interfaces" class="xliff"></a>

# Interfaces

Une ***interface*** définit un contrat qui peut être implémenté par des classes et structures. Une interface peut contenir des méthodes, des propriétés, des événements et des indexeurs. Une interface ne fournit pas les implémentations des membres qu’elle définit, elle indique simplement les membres qui doivent être fournis par les classes ou les structs qui implémentent l’interface.

Les interfaces peuvent utiliser ***l’héritage multiple***. Dans l’exemple suivant, l’interface `IComboBox` hérite à la fois de `ITextBox` et `IListBox`.

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

Les classes et les structs peuvent implémenter plusieurs interfaces. Dans l’exemple suivant, la classe `EditBox` implémente à la fois `IControl` et `IDataBound`.

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

Lorsqu’une classe ou un struct implémente une interface spécifique, les instances de cette classe ou struct peuvent être converties implicitement en ce type d’interface. Exemple :

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

Si une instance n’est pas connue pour implémenter une interface donnée de façon statique, des casts de type dynamiques peuvent être utilisés. Par exemple, les instructions suivantes utilisent des casts de type dynamiques pour obtenir les implémentations des interfaces `IControl` et `IDataBound` d’un objet. Étant donné que le type réel au moment de l’exécution de l’objet est `EditBox`, les casts réussissent.

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

Dans la classe `EditBox` précédente, la méthode `Paint` de l’interface `IControl` et la méthode `Bind` de l’interface `IDataBound` sont implémentées à l’aide des membres publics. C# prend également en charge les ***implémentations de membres d’interface*** explicites, permettant ainsi à la classe ou structure d’éviter d’avoir à créer des membres publics. Une implémentation de membre d’interface explicite est écrite à l’aide du nom de membre d’interface qualifié complet. Par exemple, la classe `EditBox` peut implémenter les méthodes `IControl.Paint` et `IDataBound.Bind` à l’aide des implémentations de membres d’interface explicites, comme suit.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

Les membres d’interface explicites sont accessibles uniquement via le type interface. Par exemple, l’implémentation de `IControl.Paint` fournie par la classe EditBox précédente ne peut être appelée en convertissant d’abord l’ `EditBox` en référence vers le type d’interface `IControl`.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
[Précédent](arrays.md)
[Suivant](enums.md)

