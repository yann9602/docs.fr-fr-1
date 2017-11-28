---
title: "Les valeurs de retour de référence et variables locales ref (Guide C#)"
description: "Découvrir comment définir et utiliser des valeurs de retour de référence et des variables locales ref"
author: rpetrusha
ms.author: ronpet
ms.date: 05/30/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 18cf7a4b-29f0-4b14-85b8-80af754aabd8
ms.openlocfilehash: 1d8fb092b578602b5d4f791a3fd14f47dfae1ba6
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="ref-returns-and-ref-locals"></a>Retours ref et variables locales ref

À compter de C# 7, C# prend en charge les valeurs de retour de référence (retours ref). Une valeur de retour de référence permet à une méthode de retourner à un appelant une référence à un objet, plutôt qu’à une valeur. L’appelant peut alors choisir de traiter l’objet retourné comme s’il était retourné par valeur ou par référence. Une valeur retournée par référence que l’appelant gère comme une référence plutôt que comme une valeur est une variable locale ref.

## <a name="what-is-a-reference-return-value"></a>Qu’est-ce qu’une valeur de retour de référence ?

La plupart des développeurs sont familiarisés avec le passage d’un argument à une méthode appelée *par référence*. La liste d’arguments d’une méthode appelée comprend une valeur passée par référence, et toute modification apportée à sa valeur par la méthode appelée est retournée à l’appelant. Une *valeur de retour de référence* est le contraire :

- La valeur de retour de la méthode appelée est une référence, et non pas un argument qui lui est passé.

- L’appelant, et non pas la méthode appelée, peut modifier la valeur retournée par la méthode.

- Au lieu que les modifications apportées à l’argument soient reflétées dans l’état de l’objet sur l’appelant, les modifications apportées à la valeur de retour de la méthode par l’appelant sont reflétées dans l’état de l’objet dont la méthode a été appelée.

Les valeurs de retour de référence peuvent produire du code plus compact, et permettre également à un objet d’exposer uniquement les éléments de données individuels, tels que d’un élément de tableau, qui sont dignes d’intérêt pour l’appelant. Cela réduit la probabilité que l’appelant modifie par inadvertance l’état de l’objet.

Certaines restrictions s’appliquent à la valeur qu’une méthode peut retourner comme valeur de retour de référence. Elles incluent notamment :

- La valeur de retour ne peut pas être `void`. Une tentative de définition d’une méthode avec une valeur de retour de référence `void` génère l’erreur du compilateur CS1547, « Le mot clé 'void' ne peut pas être utilisé dans ce contexte ».
 
- La valeur de retour ne peut pas être une variable locale dans la méthode qui la retourne. Elle doit avoir une portée située en dehors de la méthode qui la retourne. Il peut s’agir d’un champ d’instance ou statique d’une classe, ou bien un argument passé à la méthode. Une tentative de retour d’une variable locale génère l’erreur du compilateur CS8168, « Impossible de retourner la variable locale 'obj' par référence, car il ne s’agit pas d’une variable locale de référence ».

- La valeur de retour ne peut pas être `null`. Une tentative de retour de `null` génère l’erreur du compilateur CS8156, « Impossible d’utiliser une expression dans ce contexte, car elle ne peut pas être retournée par référence ».

   Si une méthode avec un retour ref doit retourner une valeur null, vous pouvez retourner une valeur null (non instanciée) pour un type référence ou un [type nullable](../nullable-types/index.md) pour un type valeur.
 
- La valeur de retour ne peut pas être une constante, un membre d’énumération ou une propriété d’un `class` ou d’un `struct`. Une tentative de retour de ces éléments génère l’erreur du compilateur CS8156, « Impossible d’utiliser une expression dans ce contexte, car elle ne peut pas être retournée par référence ».

De plus, étant donné qu’une méthode asynchrone peut retourner une valeur avant que son exécution soit terminée, alors que sa valeur de retour est toujours inconnue, les valeurs de retour de référence ne sont pas autorisées sur les méthodes async.
 
## <a name="defining-a-ref-return-value"></a>Définition d’une valeur de retour de référence

Vous définissez une valeur de retour de référence en ajoutant le mot clé [ref](../../language-reference/keywords/ref.md) au type de retour de la signature de méthode. Par exemple, la signature suivante indique que la propriété `GetContactInformation` retourne une référence à un objet `Person` à l’appelant :

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

De plus, le nom de l’objet retourné par chaque instruction [return](../../language-reference/keywords/return.md) dans le corps de la méthode doit être précédé du mot clé [ref](../../language-reference/keywords/ref.md). Par exemple, l’instruction `return` suivante retourne un objet `Person` nommé `p` par référence :

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a>Utilisation d’une valeur de retour de référence

Un appelant peut gérer une valeur de retour de référence de deux manières :

- Comme une valeur ordinaire retournée par valeur à partir d’une méthode. L’appelant peut choisir d’ignorer que la valeur de retour est une valeur de retour de référence. Dans ce cas, toute modification apportée à la valeur retournée par l’appel de méthode n’est pas reflétée dans l’état du type appelé. Si la valeur retournée est un type valeur, toute modification apportée à la valeur retournée par l’appel de méthode n’est pas reflétée dans l’état du type appelé.

- Comme valeur de retour de référence. L’appelant doit définir la variable à laquelle la valeur de retour de référence est affectée comme une [variable locale ref](#ref-local), et toute modification apportée à la valeur retournée par l’appel de méthode est reflétée dans l’état du type appelé. 

## <a name="ref-locals"></a>Variables locales ref

Pour gérer la valeur de retour de référence comme une référence, l’appelant doit déclarer la valeur comme étant une *variable locale ref* à l’aide du mot clé `ref`. Par exemple, si la valeur retournée par la méthode `Person.GetContactInfomation` doit être utilisée comme une référence plutôt que comme une valeur, l’appel de la méthode se présente ainsi :

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

Notez que le mot clé `ref` est utilisé à la fois avant la déclaration de la variable locale *et* avant l’appel de la méthode. Si les deux mots clés `ref` ne sont pas inclus dans la déclaration et l’affectation de la variable, l’erreur du compilateur CS8172, « Impossible d’initialiser une variable par référence avec une valeur » est générée. 
 
Les modifications ultérieures apportées à l’objet `Person` retourné par la méthode sont reflétées dans l’objet `contacts`.

Si `p` n’est pas défini comme une variable locale ref à l’aide du mot clé `ref`, toute modification apportée à `p` par l’appelant n’est pas reflétée dans l’objet `contacts`.
 
## <a name="ref-returns-and-ref-locals-an-example"></a>Retours ref et variables locales ref : exemple

L’exemple suivant définit une classe `NumberStore` qui stocke un tableau de valeurs entières. La méthode `FindNumber` retourne par référence le premier nombre supérieur ou égal au nombre passé comme argument. Si aucun nombre n’est supérieur ou égal à l’argument, la méthode retourne le nombre se trouvant à l’index 0. 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#1)]

L’exemple suivant appelle la méthode `NumberStore.FindNumber` pour récupérer la première valeur supérieure ou égale à 16. L’appelant multiplie ensuite par deux la valeur retournée par la méthode. Comme le montre la sortie de l’exemple, cette modification est reflétée dans la valeur des éléments de tableau de l’instance `NumberStore`.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#2)]

Si les valeurs de retour de référence ne sont pas prises en charge, une telle opération est généralement effectuée en retournant l’index de l’élément de tableau ainsi que sa valeur de retour. L’appelant peut ensuite utiliser cet index pour modifier la valeur dans un appel de méthode distinct. Toutefois, l’appelant peut également modifier l’index pour accéder à d’autres valeurs de tableau et éventuellement les modifier.  
 
## <a name="see-also"></a>Voir aussi

[ref, mot clé](../../language-reference/keywords/ref.md)
