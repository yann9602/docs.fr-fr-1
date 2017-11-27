---
title: "Conception de paramètres"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7d49c4263517830f46b1416684c7d9b874cda4db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="parameter-design"></a>Conception de paramètres
Cette section fournit des indications générales sur la conception de paramètres, y compris des sections avec des recommandations pour la vérification d’arguments. En outre, vous devez consulter les instructions décrites dans [d’affectation de noms de paramètres](../../../docs/standard/design-guidelines/naming-parameters.md).  
  
 **✓ FAIRE** utiliser le type de paramètre moins dérivé qui fournit les fonctionnalités requises par le membre.  
  
 Par exemple, supposons que vous souhaitez concevoir une méthode qui énumère une collection et imprime chaque élément dans la console. Une telle méthode doit prendre <xref:System.Collections.IEnumerable> comme paramètre, pas <xref:System.Collections.ArrayList> ou <xref:System.Collections.IList>, par exemple.  
  
 **X ne sont pas** utiliser des paramètres réservés.  
  
 Si plus d’entrée à un membre est nécessaire dans une version ultérieure, une nouvelle surcharge peut être ajoutée.  
  
 **X ne sont pas** ont exposés publiquement de méthodes qui prennent des pointeurs, des tableaux de pointeurs ou des tableaux multidimensionnels en tant que paramètres.  
  
 Pointeurs et les tableaux multidimensionnels sont relativement difficiles à utiliser correctement. Dans presque tous les cas, les API peut être modifiée pour éviter de créer ces types en tant que paramètres.  
  
 **✓ FAIRE** placer tous les `out` paramètres après toute la valeur et `ref` paramètres (à l’exclusion des tableaux de paramètres), même si cela aboutit à une incohérence dans le paramètre de classement entre les surcharges (consultez [membre La surcharge](../../../docs/standard/design-guidelines/member-overloading.md)).  
  
 Le `out` paramètres peuvent être considérées comme valeurs de retour supplémentaire, et regrouper les rend plus faciles à comprendre la signature de méthode.  
  
 **✓ FAIRE** cohérente dans les paramètres d’affectation de noms lors de la substitution de membres ou de l’implémentation des membres d’interface.  
  
 Il communique mieux la relation entre les méthodes.  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a>Choix entre l’énumération et les paramètres booléens  
 **✓ FAIRE** utiliser les énumérations si un membre possède deux ou plusieurs paramètres booléens.  
  
 **X ne sont pas** utiliser des valeurs booléennes, sauf si vous êtes absolument sûr, il y aura jamais besoin de plus de deux valeurs.  
  
 Les enums donner à la place pour l’ajout ultérieur de valeurs, mais vous devez être conscient de toutes les implications de l’ajout de valeurs aux énumérations, qui sont décrites dans [Enum conception](../../../docs/standard/design-guidelines/enum.md).  
  
 **✓ Envisagez** à l’aide de valeurs booléennes pour les paramètres du constructeur qui sont des valeurs de deux États réellement et sont uniquement utilisées pour initialiser les propriétés booléennes.  
  
### <a name="validating-arguments"></a>Validation d’Arguments  
 **✓ FAIRE** valider les arguments passés aux membres publics, protégés ou implémentées explicitement. Lever <xref:System.ArgumentException?displayProperty=nameWithType>, ou une de ses sous-classes, si la validation échoue.  
  
 Notez que la validation réelle ne doit pas nécessairement se produire dans le membre public ou protégé proprement dit. Il peut se produire à un niveau inférieur dans une routine privé ou interne. Le point essentiel est que toute la surface exposée aux utilisateurs finaux vérifie les arguments.  
  
 **✓ FAIRE** lever <xref:System.ArgumentNullException> si un argument null est passé et le membre ne prend pas en charge les arguments null.  
  
 **✓ FAIRE** valider les paramètres d’énumération.  
  
 Ne supposez pas arguments enum seront dans la plage définie par l’énumération. Le CLR permet d’effectuer un cast d’une valeur entière en une valeur d’énumération même si la valeur n’est pas définie dans l’énumération.  
  
 **X ne sont pas** utiliser <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> pour la plage enum vérifie.  
  
 **✓ FAIRE** Sachez que les arguments mutables peuvent ont été modifiés après leur validation.  
  
 Si le membre est sensible à la sécurité, il est conseillé d’effectuer une copie puis valider et traiter l’argument.  
  
### <a name="parameter-passing"></a>Passage de paramètres  
 À partir de la perspective d’un concepteur de framework, il existe trois principaux groupes de paramètres : les paramètres, par valeur `ref` paramètres, et `out` paramètres.  
  
 Lorsqu’un argument est passé via un paramètre par valeur, le membre reçoit une copie de l’argument réel passé. Si l’argument est un type valeur, une copie de l’argument est placée sur la pile. Si l’argument est un type référence, une copie de la référence est placée sur la pile. Les plus populaires CLR langages, tels que c#, VB.NET et C++, par défaut pour le passage de paramètres par valeur.  
  
 Lorsqu’un argument est passé via un `ref` paramètre, le membre reçoit une référence à l’argument réel passé. Si l’argument est un type valeur, une référence à l’argument est placée sur la pile. Si l’argument est un type référence, une référence à la référence est placée sur la pile. `Ref`paramètres peuvent être utilisés pour permettre au membre de modifier les arguments passés par l’appelant.  
  
 `Out`les paramètres sont similaires à `ref` paramètres, avec de petites différences. Le paramètre est considéré comme initialement non assigné et ne peut pas être lu dans le corps du membre avant de l’assigner une valeur. En outre, le paramètre a à assigner une valeur avant le retour du membre.  
  
 **X Évitez** à l’aide de `out` ou `ref` paramètres.  
  
 À l’aide de `out` ou `ref` paramètres nécessite une certaine expérience des pointeurs, de comprendre la différence entre les types valeur et les types référence et la gestion de méthodes impliquant plusieurs valeurs de retour. En outre, la différence entre `out` et `ref` paramètres est généralement peu comprise. Architectes de Framework conception destiné à une audience générale ne doivent pas s’attendre aux utilisateurs maîtrisent l’utilisation des `out` ou `ref` paramètres.  
  
 **X ne sont pas** passage de types référence par référence.  
  
 Il existe quelques exceptions limitées à la règle, tel qu’une méthode qui peut être utilisée pour échanger des références.  
  
### <a name="members-with-variable-number-of-parameters"></a>Membres avec un nombre Variable de paramètres  
 Les membres qui peuvent prendre un nombre variable d’arguments sont exprimées en fournissant un paramètre de tableau. Par exemple, <xref:System.String> fournit la méthode suivante :  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 Un utilisateur peut ensuite appeler la <xref:System.String.Format%2A?displayProperty=nameWithType> méthode, comme suit :  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 Ajoutez le mot clé c# params à un paramètre de tableau modifie le paramètre à un paramètre de tableau params soi-disant et fournit un raccourci vers la création d’un tableau temporaire.  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 Cela permet à l’utilisateur à appeler la méthode en passant les éléments du tableau directement dans la liste d’arguments.  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 Notez que le mot clé params peut être ajouté uniquement au dernier paramètre dans la liste de paramètres.  
  
 **✓ Envisagez** Ajout du mot clé params aux paramètres de tableau, si vous pensez que les utilisateurs finaux pour passer des tableaux avec un petit nombre d’éléments. S’il est prévu qu’un grand nombre d’éléments est passé en commun des scénarios, les utilisateurs sans doute ne passera pas inline de ces éléments quand même et par conséquent, le mot clé params n’est pas nécessaire.  
  
 **X Évitez** à l’aide de tableaux params si l’appelant est presque toujours avoir l’entrée dans un tableau.  
  
 Par exemple, les membres avec des paramètres de tableau d’octets seraient presque jamais être appelées en passant des octets individuels. Pour cette raison, les paramètres de tableau d’octets dans le .NET Framework n’utilisent pas le mot clé params.  
  
 **X ne sont pas** utiliser des tableaux params si le tableau est modifié par le membre prenant le paramètre de tableau params.  
  
 En raison du fait que de nombreux compilateurs activer les arguments pour le membre dans un tableau temporaire sur le site d’appel, le tableau peut être un objet temporaire, et par conséquent, toute modification du tableau seront perdues.  
  
 **✓ Envisagez** à l’aide du mot clé params dans une surcharge simple, même si une surcharge plus complexe ne peut pas l’utiliser.  
  
 Demandez-vous si les utilisateurs seraient valeur ayant le tableau params dans une surcharge, même si elle n’était pas dans toutes les surcharges.  
  
 **✓ FAIRE** essayez des paramètres de commande pour le rendre possible d’utiliser le mot clé params.  
  
 **✓ Envisagez** fournissant des surcharges spéciaux et les chemins de code pour les appels avec un petit nombre d’arguments dans les API très sensibles aux performances.  
  
 Cela rend possible pour éviter de créer des objets de tableau lors de l’API est appelée avec un petit nombre d’arguments. Forment les noms des paramètres en prenant la forme au singulier du paramètre de tableau et en ajoutant un suffixe numérique.  
  
 Vous devez le faire uniquement si vous vous apprêtez à des cas spéciaux le chemin d’accès de l’ensemble du code, pas seulement de créer un tableau et appeler la méthode la plus générale.  
  
 **✓ FAIRE** Sachez que la valeur null peut être passée comme un argument de tableau params.  
  
 Vous devez valider que le tableau n’est pas null avant le traitement.  
  
 **X ne sont pas** utiliser le `varargs` méthodes en tant que les points de suspension.  
  
 Certains langages CLR, tels que C++, prennent en charge une autre convention pour passer des listes de paramètres de variable appelées `varargs` méthodes. La convention ne doit pas utilisable dans les infrastructures, car il n’est pas conforme.  
  
### <a name="pointer-parameters"></a>Paramètres de pointeur  
 En règle générale, les pointeurs ne doivent pas apparaître dans la surface publique d’une infrastructure bien conçue du code managé. La plupart du temps, les pointeurs doivent être encapsulées. Toutefois, dans certains cas, des pointeurs sont requis pour des raisons de l’interopérabilité et l’utilisation des pointeurs dans ce cas est appropriée.  
  
 **✓ FAIRE** offrent une alternative pour les membres qui prennent un argument de pointeur, étant donné que les pointeurs ne sont pas conformes CLS.  
  
 **X Évitez** effectuant l’argument coûteux, la vérification des arguments de pointeur.  
  
 **✓ FAIRE** suivent les conventions de pointeur associé courantes lors de la conception de membres avec des pointeurs.  
  
 Par exemple, il n’est pas nécessaire de passer de l’index de début, car l’opération arithmétique de pointeur simple peut être utilisé pour accomplir le même résultat.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de membres](../../../docs/standard/design-guidelines/member.md)  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
