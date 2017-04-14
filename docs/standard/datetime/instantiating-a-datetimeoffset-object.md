---
title: "Instanciation d&#39;un objet DateTimeOffset | Microsoft Docs"
ms.custom: ""
ms.date: "04/10/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instancier des objets de fuseau horaire"
  - "objet de fuseau horaire (.NET Framework), instanciation"
  - "DateTimeOffset (structure), conversion en DateTime"
  - "DateTimeOffset (structure), instanciation"
ms.assetid: 9648375f-d368-4373-a976-3332ece00c0a
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# Instanciation d&#39;un objet DateTimeOffset
La structure <xref:System.DateTimeOffset> permet de créer des valeurs <xref:System.DateTimeOffset> de plusieurs manières.  La plupart d'entre elles correspondent directement aux méthodes d'instanciation de nouvelles valeurs <xref:System.DateTime> qui sont disponibles, avec des améliorations qui vous permettent de spécifier le décalage de la valeur de date et d'heure par rapport au temps universel coordonné \(UTC, Coordinated Universal Time\).  Vous pouvez notamment instancier une valeur <xref:System.DateTimeOffset> de différentes manières :  
  
-   en utilisant un littéral de date et d'heure ;  
  
-   en appelant un constructeur <xref:System.DateTimeOffset>;  
  
-   en convertissant implicitement une valeur en valeur <xref:System.DateTimeOffset>;  
  
-   en analysant la représentation sous forme de chaîne d'une date et d'une heure.  
  
 Cette rubrique fournit des informations détaillées, ainsi que des exemples de code qui illustrent ces méthodes d'instanciation de nouvelles valeurs <xref:System.DateTimeOffset>.  
  
## Littéraux de date et d'heure  
 Pour les langages qui prennent en charge les littéraux, l'une des méthodes d'instanciation d'une valeur <xref:System.DateTime> les plus courantes consiste à fournir la date et l'heure sous la forme d'une valeur de littéral codé en dur.  Par exemple, le code Visual Basic suivant crée un objet <xref:System.DateTime> dont la valeur est le 1er janvier 2008, à 10 h.  
  
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]  
  
 Les valeurs <xref:System.DateTimeOffset> peuvent également être initialisées à l'aide de littéraux de date et d'heure lorsque des langages prenant en charge des littéraux <xref:System.DateTime> sont utilisés.  Par exemple, le code Visual Basic suivant crée un objet <xref:System.DateTimeOffset>.  
  
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]  
  
 Comme la sortie de la console l'indique, le décalage du fuseau horaire local est assigné à la valeur <xref:System.DateTimeOffset> créée de cette manière.  Cela signifie qu'une valeur <xref:System.DateTimeOffset> assignée à l'aide d'un littéral de caractère n'identifie pas un point unique dans le temps lorsque le code est exécuté sur des ordinateurs différents.  
  
## Constructeurs DateTimeOffset  
 Le type <xref:System.DateTimeOffset> définit six constructeurs.  Quatre d'entre eux correspondent directement aux constructeurs <xref:System.DateTime>, avec un paramètre supplémentaire de type <xref:System.TimeSpan> qui définit le décalage de date et d'heure par rapport à l'heure UTC.  Ceux\-ci vous permettent de définir une valeur <xref:System.DateTimeOffset> en fonction de la valeur de chacun de ses composants de date et d'heure.  Par exemple, le code suivant utilise ces quatre constructeurs pour instancier des objets <xref:System.DateTimeOffset> avec des valeurs identiques de 7\/1\/2008 12:05 AM \+ 01: 00.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]  
  
 Notez que lorsque la valeur de l'objet <xref:System.DateTimeOffset> instancié à l'aide d'un objet <xref:System.Globalization.PersianCalendar> en tant que l'un des arguments à son constructeur est affichée dans la console, elle est exprimée sous la forme d'une date du calendrier grégorien plutôt que du calendrier persan.  Pour obtenir une date à l'aide du calendrier persan, consultez l'exemple illustré dans la rubrique <xref:System.Globalization.PersianCalendar>.  
  
 Les deux autres constructeurs créent un objet <xref:System.DateTimeOffset> à partir d'une valeur <xref:System.DateTime>.  Le premier des deux possède un paramètre unique, la valeur <xref:System.DateTime> à convertir en valeur <xref:System.DateTimeOffset>.  Le décalage de la valeur <xref:System.DateTimeOffset> résultante dépend de la propriété <xref:System.DateTime.Kind%2A> du paramètre unique du constructeur.  Si sa valeur est <xref:System.DateTimeKind?displayProperty=fullName>, le décalage a la valeur <xref:System.TimeSpan.Zero?displayProperty=fullName>.  Sinon, son décalage a la valeur du fuseau horaire local.  L'exemple suivant illustre l'utilisation de ce constructeur pour instancier des objets <xref:System.DateTimeOffset> qui représentent l'heure UTC et le fuseau horaire local :  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]  
  
> [!NOTE]
>  L'appel de la surcharge du constructeur <xref:System.DateTimeOffset> qui possède un paramètre <xref:System.DateTime> unique équivaut à l'exécution d'une conversion implicite d'une valeur <xref:System.DateTime> en valeur <xref:System.DateTimeOffset>.  
  
 Le deuxième constructeur qui crée un objet <xref:System.DateTimeOffset> à partir d'une valeur <xref:System.DateTime> possède deux paramètres : la valeur <xref:System.DateTime> à convertir et une valeur <xref:System.TimeSpan> qui représente le décalage de date et d'heure par rapport à l'heure UTC.  Cette valeur de décalage doit correspondre à la propriété <xref:System.DateTime.Kind%2A> du premier paramètre du constructeur, sinon un <xref:System.ArgumentException> est levé.  Si la propriété <xref:System.DateTime.Kind%2A> du premier paramètre est <xref:System.DateTimeKind?displayProperty=fullName>, la valeur du deuxième paramètre doit être <xref:System.TimeSpan.Zero?displayProperty=fullName>.  Si la propriété <xref:System.DateTime.Kind%2A> du premier paramètre est <xref:System.DateTimeKind?displayProperty=fullName>, la valeur du deuxième paramètre doit correspondre au décalage du fuseau horaire du système local.  Si la propriété <xref:System.DateTime.Kind%2A> du premier paramètre a la valeur <xref:System.DateTimeKind?displayProperty=fullName>, le décalage peut être équivalent à toute valeur valide.  Le code suivant illustre des appels à ce constructeur pour convertir <xref:System.DateTime> en valeurs <xref:System.DateTimeOffset>.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]  
  
## Conversion de type implicite  
 Le type <xref:System.DateTimeOffset> prend en charge une conversion de type implicite : d'une valeur <xref:System.DateTime> en valeur <xref:System.DateTimeOffset>. Une conversion de type implicite est une conversion d'un type dans un autre qui ne requiert pas de cast explicite \(en C\#\) ni de conversion \(dans Visual Basic\) et qui ne perd pas d'informations.  Grâce à elle, le code suivant est possible.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]  
  
 Le décalage de la valeur <xref:System.DateTimeOffset> résultante dépend de la valeur de propriété <xref:System.DateTime.Kind%2A?displayProperty=fullName>.  Si sa valeur est <xref:System.DateTimeKind?displayProperty=fullName>, le décalage a la valeur <xref:System.TimeSpan.Zero?displayProperty=fullName>.  Si sa valeur est <xref:System.DateTimeKind?displayProperty=fullName> ou <xref:System.DateTimeKind?displayProperty=fullName>, le décalage a la valeur du fuseau horaire local.  
  
## Analyse de la représentation sous forme de chaîne d'une date et d'une heure  
 Le type <xref:System.DateTimeOffset> prend en charge quatre méthodes qui vous permettent de convertir la représentation sous forme de chaîne d'une date et d'une heure en valeur <xref:System.DateTimeOffset>:  
  
-   <xref:System.DateTimeOffset.Parse%2A>, qui essaie de convertir la représentation sous forme de chaîne d'une date et d'une heure en valeur <xref:System.DateTimeOffset> et lève une exception en cas d'échec de la conversion.  
  
-   <xref:System.DateTimeOffset.TryParse%2A>, qui essaie de convertir la représentation sous forme de chaîne d'une date et d'une heure en valeur <xref:System.DateTimeOffset> et retourne `false` en cas d'échec de la conversion.  
  
-   <xref:System.DateTimeOffset.ParseExact%2A>, qui essaie de convertir la représentation sous forme de chaîne d'une date et d'une heure dans un format spécifié en valeur <xref:System.DateTimeOffset>.  Cette méthode lève une exception en cas d'échec de la conversion.  
  
-   <xref:System.DateTimeOffset.TryParseExact%2A>, qui essaie de convertir la représentation sous forme de chaîne d'une date et d'une heure dans un format spécifié en valeur <xref:System.DateTimeOffset>.  La méthode retourne `false` en cas d'échec de la conversion.  
  
 L'exemple suivant illustre des appels à chacune de ces quatre méthodes de conversion de chaînes pour instancier une valeur <xref:System.DateTimeOffset>.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]  
  
## Voir aussi  
 [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)