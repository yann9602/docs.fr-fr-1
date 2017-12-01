---
title: "Sémantique de référence avec les types valeur"
description: "Comprendre les fonctionnalités de langage qui réduisent les structures de copie en toute sécurité"
author: billwagner
ms.author: wiwagn
ms.date: 11/10/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 9eeaf201c1f5a58044db62e356199b609c4c035a
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="reference-semantics-with-value-types"></a>Sémantique de référence avec les types valeur

L’avantage de l’utilisation des types de valeur est qu’ils évitent d’allocations de tas.
L’inconvénient correspondante est qu’elles sont copiées par valeur. Ce compromis rend plus difficile optimiser les algorithmes qui fonctionnent sur de grandes quantités de données. Nouvelles fonctionnalités de langage c# 7.2 fournissent des mécanismes qui permettent la sémantique de passage par référence avec les types valeur. Si vous utilisez ces fonctionnalités avec soin, vous pouvez réduire les allocations et opérations de copie. Cet article explore ces nouvelles fonctionnalités.

Une grande partie de l’exemple de code dans cet article montre les fonctionnalités ajoutées dans c# 7.2. Pour pouvoir utiliser ces fonctionnalités, vous devez configurer votre projet pour utiliser le langage c# 7.2 ou version ultérieure dans votre projet. Vous pouvez utiliser Visual Studio pour le sélectionner. Pour chaque projet, sélectionnez **projet** dans le menu, puis **propriétés**. Sélectionnez le **générer** onglet et cliquez sur **avancé**. À partir de là, vous pouvez configurer la version de langue. Choisissez « 7.2 », ou « dernier ».  Vous pouvez aussi modifier la *csproj* et ajoutez le nœud suivant :

```XML
  <PropertyGroup>
    <LangVersion>7.2</LangVersion>
  </PropertyGroup>
```

Vous pouvez utiliser « 7.2 » ou « dernier » pour la valeur.

## <a name="specifying-in-parameters"></a>Spécification `in` paramètres

7.2 c# ajoute le `in` (mot clé) pour compléter existants `ref` et `out` mots clés lorsque vous écrivez une méthode qui transmet des arguments par référence. Le `in` mot clé spécifie que vous passez le paramètre par référence et la méthode appelée ne modifie pas la valeur passée à ce dernier. 

Cet ajout fournit un vocabulaire complète pour exprimer votre intention de conception. Types valeur sont copiés quand il est passé à une méthode appelée lorsque vous ne spécifiez pas un des modificateurs suivants. Chacune de ces modificateurs de spécifier qu’un type valeur est passé par référence, évitant ainsi la copie. Chaque modificateur exprime un objectif différent :

- `out`: Cette méthode définit la valeur de l’argument utilisé en tant que ce paramètre.
- `ref`: Cette méthode peut définir la valeur de l’argument utilisé en tant que ce paramètre.
- `in`: Cette méthode ne modifie pas la valeur de l’argument utilisé en tant que ce paramètre.

Lorsque vous ajoutez le `in` modificateur pour passer un argument par référence, vous déclarez votre objectif de conception est de passer des arguments par référence afin d’éviter la copie inutile. Vous ne souhaitez pas modifier l’objet utilisé comme argument. Le code suivant montre un exemple d’une méthode qui calcule la distance entre deux points dans un espace 3D. 

[!code-csharp[InArgument](../../samples/csharp/reference-semantics/Program.cs#InArgument "Specifying an In argument")]

Les arguments sont deux structures qui contiennent chacune des trois valeurs de type double. Un double est de 8 octets, par conséquent, chaque argument est de 24 octets. En spécifiant le `in` modificateur, que vous passez une référence codés sur 4 ou 8 octets pour ces arguments, selon l’architecture de l’ordinateur. La différence de taille est faible, mais elle peut rapidement s’ajouter lorsque votre application appelle cette méthode dans une boucle serrée, à l’aide de nombreuses valeurs différentes.
 
Le `in` modificateur complète `out` et `ref` d’autres façons. Vous ne pouvez pas créer de surcharges d’une méthode qui diffèrent uniquement en présence de `in`, `out` ou `ref`. Ces nouvelles règles d’étendent le comportement de même a toujours été défini pour `out` et `ref` paramètres.

Le `in` modificateur peut être appliqué à n’importe quel membre qui accepte des paramètres : méthodes, les délégués, les expressions lambda, fonctions locales, indexeurs, opérateurs.

Contrairement aux `ref` et `out` arguments, vous pouvez utiliser les valeurs littérales ou des constantes pour l’argument à un `in` paramètre. En outre, contrairement à un `ref` ou `out` paramètre, vous n’avez pas besoin d’appliquer le `in` modificateur sur le site d’appel. Le code suivant présente deux exemples de l’appel de la `CalculateDistance` (méthode). Le premier délégué utilise deux variables locales, passés par référence. La deuxième inclut une variable temporaire est créée dans le cadre de l’appel de méthode. 

[!code-csharp[UseInArgument](../../samples/csharp/reference-semantics/Program.cs#UseInArgument "Specifying an In argument")]

Il existe plusieurs façons dans lequel le compilateur garantit que la nature en lecture seule d’un `in` argument est appliqué.  Tout d’abord, la méthode appelée ne peut pas attribuer directement à un `in` paramètre. Il ne peut pas attribuer directement à n’importe quel champ d’un `in` paramètre. En outre, vous ne pouvez pas passer un `in` paramètre à toute méthode en exigeant la `ref` ou `out` modificateur.
Le compilateur considère que la `in` argument est une variable en lecture seule. Vous pouvez appeler toute méthode d’instance qui utilise une sémantique de passage par valeur. Dans ce cas, une copie de la `in` paramètre est créé. Étant donné que le compilateur peut créer une variable temporaire pour les `in` paramètre, vous pouvez également spécifier des valeurs par défaut pour toute `in` paramètre. Le code suivant qui utilise pour spécifier l’origine (point 0,0) comme valeur par défaut pour le deuxième point :

[!code-csharp[InArgumentDefault](../../samples/csharp/reference-semantics/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Le `in` désignation de paramètre peut également être utilisée avec les types référence ou générée dans les valeurs numériques. Toutefois, les avantages dans les deux cas sont minimes, le cas échéant.

## <a name="ref-readonly-returns"></a>`ref readonly`Retourne

Vous pouvez souhaiter également un type de valeur de retour par référence, mais ne pas autoriser l’appelant à partir de la modification de cette valeur. Utilisez le `ref readonly` modificateur pour exprimer l’intention de cette conception. Il indique aux lecteurs que vous ne retournant une référence aux données existantes, mais autorise ne pas la modification. 

Le compilateur impose que l’appelant ne peut pas modifier la référence. Tente d’assigner directement à la valeur génère une erreur de compilation. Toutefois, le compilateur ne peut pas savoir si n’importe quelle méthode membre modifie l’état de la structure.
Pour vous assurer que l’objet n’est pas modifié, le compilateur crée une copie et appelle des références à l’aide de cette copie de membre. Les modifications sont à la copie. 

Il est probable que la bibliothèque à l’aide `Point3D` utiliseriez souvent l’origine dans le code. Chaque instance crée un nouvel objet dans la pile. Il peut être avantageux de créer une constante et la retournez par référence. Toutefois, si vous retournez une référence à un stockage interne, il pouvez que vous souhaitez appliquer que l’appelant ne peut pas modifier le stockage référencé. Le code suivant définit une propriété en lecture seule qui renvoie une `readonly ref` à un `Point3D` qui spécifie l’origine.

[!code-csharp[OriginReference](../../samples/csharp/reference-semantics/Point3D.cs#OriginReference "Creating a readonly Origin reference")]

Il est facile de créer une copie d’une readonly ref retour : simplement l’affecter à une variable non déclarée avec le `ref readonly` modificateur. Le compilateur génère du code pour copier l’objet dans le cadre de l’affectation. 

Lorsque vous assignez une variable à un `ref readonly return`, vous pouvez spécifier une `ref readonly` variable ou une copie par valeur de la référence en lecture seule :

[!code-csharp[AssignRefReadonly](../../samples/csharp/reference-semantics/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

La première assignation dans le code précédent effectue une copie de la `Origin` constante et affecte cette copie. La seconde assigne une référence. Notez que le `readonly` modificateur doit faire partie de la déclaration de la variable. La référence à laquelle il fait référence ne peut pas être modifiée. Tente de faire provoque une erreur de compilation.

## <a name="readonly-struct-type"></a>Type `readonly struct`

Application `ref readonly` à fort trafic des utilisations d’un struct peut suffire.
Parfois, vous voudrez créer un struct immuable. Ensuite, vous pouvez toujours passer par référence d’en lecture seule. Que pratique supprime la défense de copie qui se produisent lorsque vous accédez aux méthodes d’un struct utilisé comme un `in` paramètre.

Que faire, vous pouvez créer un `readonly struct` type. Vous pouvez ajouter la `readonly` modificateur à une déclaration de struct. Le compilateur impose que tous les membres du struct sont `readonly`; le `struct` doivent être immuables.

Il existe d’autres optimisations pour un `readonly struct`. Vous pouvez utiliser la `in` modificateur à chaque emplacement où un `readonly struct` est un argument. En outre, vous pouvez retourner un `readonly struct` comme un `ref return` lorsque vous retournez un objet dont durée de vie s’étend au-delà de la portée de la méthode de retour de l’objet.

Enfin, le compilateur génère du code plus efficace lorsque vous appelez des membres d’un `readonly struct`: le `this` référence, au lieu d’une copie du récepteur, est toujours un `in` paramètre passé par référence à la méthode de membre. Cette optimisation enregistre une copie plus lorsque vous utilisez un `readonly struct`. Le `Point3D` est un bon candidat pour que cette modification. Le code suivant illustre une mise à jour `ReadonlyPoint3D` structure :

[!code-csharp[ReadonlyOnlyPoint3D](../../samples/csharp/reference-semantics/Point3D.cs#ReadonlyOnlyPoint3D "Defining an immutable structure")]

## <a name="ref-struct-type"></a>Type `ref struct`

Une autre fonctionnalité de langage associé est la possibilité de déclarer un type valeur qui doit être allouée à la pile. En d’autres termes, ces types ne peuvent jamais être créés sur le tas en tant que membre d’une autre classe. L’objectif principal de cette fonctionnalité a été <xref:System.Span%601> et les structures associées. <xref:System.Span%601>peut contenir un pointeur managé comme l’un de ses membres, l’autre étant la longueur de l’étendue. Il est implémenté en fait un peu différemment, car c# ne prend en charge des pointeurs vers la mémoire managée en dehors d’un contexte unsafe. Toute écriture qui modifie le pointeur et la longueur n’est pas atomique. Cela signifie une <xref:System.Span%601> serait soumis à des erreurs de plage insuffisante ou d’autres violations de sécurité de type ont été il pas limité à un frame de pile. En outre, placer un pointeur managé sur le tas GC généralement se bloque au moment de JIT.

Vous pouvez avoir des exigences similaires fonctionne avec créé à l’aide de la mémoire [ `stackalloc` ](language-reference/keywords/stackalloc.md) ou lors de l’utilisation de mémoire à partir de l’API d’interopérabilité. Vous pouvez définir vos propres `ref struct` types à ces besoins. Dans cet article, vous consultez des exemples d’utilisation de `Span<T>` par souci de simplicité.

Le `ref struct` déclaration déclare qu’une structure de ce type doit être sur la pile. Les règles de langage l’assurer le bon fonctionnement de ces types. Autres types déclarés en tant que `ref struct` incluent <xref:System.ReadOnlySpan%601>. 

Le but de conserver un `ref struct` type telle qu’une variable allouée à la pile introduit plusieurs règles que le compilateur applique pour tous les `ref struct` types.

- Vous ne peut pas convertir un `ref struct`. Vous ne pouvez pas affecter un `ref struct` type dans une variable de type `object`, `dynamic`, ou n’importe quel type interface.
- Vous ne pouvez pas déclarer un `ref struct` en tant que membre d’une classe ou un struct normal.
- Vous ne pouvez pas déclarer des variables locales sont `ref struct` types dans les méthodes async. Vous pouvez les déclarer dans des méthodes synchrones qui retournent `Task`, `Task<T>` ou les types de tâches.
- Vous ne pouvez pas déclarer `ref struct` variables locales dans les itérateurs.
- Vous ne pouvez pas capturer `ref struct` variables dans les expressions lambda ou de fonctions locales.

Ces restrictions s’assurer que vous n’utilisez pas accidentellement un `ref struct` d’une manière qui pourrait le promouvoir pour le tas managé.

## <a name="conclusions"></a>Conclusions

Ces améliorations du langage c# sont conçues pour les algorithmes de performances critiques où les allocations de mémoire peuvent être essentielles d’atteindre les performances nécessaires. Vous constaterez peut-être que vous n’utilisez pas souvent ces fonctionnalités dans le code que vous écrivez. Toutefois, ces améliorations ont été adoptées à de nombreux emplacements dans le .NET Framework. Comme les API d’utiliser ces fonctionnalités, vous verrez les performances de vos propres applications améliorer.
