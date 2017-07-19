---
title: "Conception de param&#232;tres | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "règles de conception de membres (.NET Framework), paramètres"
  - "membres (.NET Framework), paramètres"
  - "noms (.NET Framework), paramètres"
  - "paramètres, des règles de conception"
  - "paramètres réservés"
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Conception de param&#232;tres
Cette section fournit des conseils généraux sur la conception de paramètres, y compris des sections avec des instructions concernant la vérification d’arguments. En outre, consultez les instructions décrites dans [Paramètres d’affectation de noms](../../../docs/standard/design-guidelines/naming-parameters.md).  
  
 **✓ faire** utiliser le type de paramètre moins dérivé qui fournit les fonctionnalités requises par le membre.  
  
 Par exemple, supposons que vous souhaitez créer une méthode qui énumère la collection et imprime chaque élément dans la console. Une telle méthode doit prendre <xref:System.Collections.IEnumerable> comme paramètre, pas <xref:System.Collections.ArrayList> ou <xref:System.Collections.IList>, par exemple.  
  
 **X ne pas** utiliser des paramètres réservés.  
  
 Si plusieurs entrées à un membre sont nécessaire dans une version ultérieure, une nouvelle surcharge peut être ajoutée.  
  
 **X ne pas** ont exposés publiquement de méthodes qui prennent des pointeurs, des tableaux de pointeurs ou des tableaux multidimensionnels en tant que paramètres.  
  
 Pointeurs et les tableaux multidimensionnels sont relativement difficiles à utiliser correctement. Dans presque tous les cas, les API permettre être refondu pour éviter de créer ces types en tant que paramètres.  
  
 **✓ faire** placer tous les `out` paramètres après toute la valeur et `ref` Paramètres \(à l’exclusion des tableaux de paramètres\), même s’il en résulte une incohérence dans le paramètre de classement entre les surcharges \(voir [Surcharge de membre](../../../docs/standard/design-guidelines/member-overloading.md)\).  
  
 Le `out` paramètres peuvent être considérées comme des valeurs de retour supplémentaire et regroupant rend la signature de méthode plus facile à comprendre.  
  
 **✓ faire** être cohérente dans les paramètres d’affectation de noms lors de la substitution de membres ou de l’implémentation de membres d’interface.  
  
 Il communique mieux la relation entre les méthodes.  
  
### Choix entre Enum et des paramètres booléens  
 **✓ faire** utiliser les énumérations si un membre aura deux ou plusieurs paramètres booléens.  
  
 **X ne pas** utiliser des valeurs booléennes, sauf si vous êtes absolument certain, il ne sera jamais besoin de plus de deux valeurs.  
  
 Enums donner à la place pour l’ajout ultérieur de valeurs, mais vous devez être conscient de toutes les implications de l’ajout de valeurs aux énumérations, qui sont décrites dans [Conception d’énumérations](../../../docs/standard/design-guidelines/enum.md).  
  
 **✓ envisagez** à l’aide de valeurs booléennes pour les paramètres de constructeur sont véritablement deux États qui sont uniquement utilisées pour initialiser les propriétés booléennes.  
  
### Validation d’Arguments  
 **✓ faire** valider les arguments passés aux membres publics, protégés ou implémentées explicitement. Lever <xref:System.ArgumentException?displayProperty=fullName>, ou une de ses sous\-classes, si la validation échoue.  
  
 Notez que la validation réelle ne doit pas nécessaire se produire dans le membre public ou protégé lui\-même. Ceci peut être dû à un niveau inférieur dans une routine privé ou interne. L’essentiel est que toute la surface exposée aux utilisateurs finaux vérifie les arguments.  
  
 **✓ faire** lever <xref:System.ArgumentNullException> Si un argument null est passé et que le membre ne prend pas en charge les arguments null.  
  
 **✓ faire** valider les paramètres de l’enum.  
  
 Ne supposez pas arguments enum seront dans la plage définie par l’énumération. Le CLR permet d’effectuer un cast d’une valeur entière en une valeur d’énumération même si la valeur n’est pas définie dans l’énumération.  
  
 **X ne pas** utiliser <xref:System.Enum.IsDefined%2A?displayProperty=fullName> plage d’énumération des vérifications.  
  
 **✓ faire** n’oubliez pas que les arguments mutables peuvent ont changé après leur validation.  
  
 Si le membre est sensible à la sécurité, il est recommandé d’effectuer une copie puis valider et traiter l’argument.  
  
### Passage de paramètres  
 Du point de vue d’un concepteur de framework, il existe trois principaux groupes de paramètres : les paramètres, par valeur `ref` paramètres, et `out` paramètres.  
  
 Lorsqu’un argument est transmis via un paramètre par valeur, le membre reçoit une copie de l’argument réel passé. Si l’argument est un type valeur, une copie de l’argument est placée sur la pile. Si l’argument est un type référence, une copie de la référence est placée sur la pile. Langages CLR plus populaires, tels que c\#, VB.NET et C\+\+, valeur par défaut pour passer des paramètres par valeur.  
  
 Lorsqu’un argument est passé via un `ref` paramètre, le membre reçoit une référence à l’argument réel passé. Si l’argument est un type valeur, une référence à l’argument est placée sur la pile. Si l’argument est un type référence, une référence à la référence est placée sur la pile.`Ref` paramètres peuvent être utilisés pour permettre au membre de modifier les arguments passés par l’appelant.  
  
 `Out` les paramètres sont similaires à `ref` paramètres, avec de petites différences. Le paramètre est considéré comme initialement non assigné et ne peut pas être lu dans le corps du membre avant de l’assigner une valeur. En outre, le paramètre a à assigner une valeur avant le retour du membre.  
  
 **X éviter** à l’aide de `out` ou `ref` paramètres.  
  
 À l’aide de `out` ou `ref` paramètres nécessite une certaine expérience des pointeurs, de comprendre la différence entre les types valeur et types référence et la gestion de méthodes impliquant plusieurs valeurs de retour. En outre, la différence entre `out` et `ref` paramètres est généralement peu comprise. Les architectes d’infrastructure conception destiné à une audience générale ne doivent pas s’attendre aux utilisateurs maîtrisent l’utilisation des `out` ou `ref` paramètres.  
  
 **X ne pas** passer les types référence par référence.  
  
 Il existe quelques rares exceptions à la règle, comme une méthode qui peut être utilisée pour échanger des références.  
  
### Membres avec un nombre Variable de paramètres  
 Les membres qui peuvent prendre un nombre variable d’arguments sont exprimées en fournissant un paramètre de tableau. Par exemple, <xref:System.String> fournit la méthode suivante :  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 Un utilisateur peut ensuite appeler la <xref:System.String.Format%2A?displayProperty=fullName> méthode, comme suit :  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 Ajoutez le mot clé c\# params pour un paramètre de tableau modifie le paramètre à un paramètre de tableau params soi\-disant et fournit un raccourci pour créer un tableau temporaire.  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 Cela permet à l’utilisateur d’appeler la méthode en transmettant les éléments du tableau directement dans la liste d’arguments.  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 Notez que le mot clé params peut être ajouté uniquement pour le dernier paramètre dans la liste de paramètres.  
  
 **✓ envisagez** Ajout du mot clé params aux paramètres de tableau si vous pensez que les utilisateurs finaux pour passer des tableaux avec un petit nombre d’éléments. S’il est prévu qu’un grand nombre d’éléments est passé en commun des scénarios, les utilisateurs sans doute ne passera pas inline de ces éléments quand même et le mot clé params n’est donc pas nécessaire.  
  
 **X éviter** à l’aide de tableaux params si l’appelant est presque toujours avoir l’entrée dans le tableau.  
  
 Par exemple, les membres avec des paramètres de tableau d’octets presque jamais appelés en passant des octets. Pour cette raison, les paramètres de tableau d’octets dans le .NET Framework n’utilisent pas le mot clé params.  
  
 **X ne pas** utiliser des tableaux params si le tableau est modifié par le membre prenant le paramètre de tableau params.  
  
 En raison du fait que de nombreux compilateurs activer les arguments pour le membre dans un tableau temporaire sur le site d’appel, le tableau peut être un objet temporaire, et par conséquent, toute modification du tableau seront perdues.  
  
 **✓ envisagez** à l’aide du mot clé params dans une surcharge simple, même si une surcharge plus complexe ne peut pas l’utiliser.  
  
 Demandez\-vous si les utilisateurs seraient valeur ayant le tableau params dans une surcharge même si ce n’était pas dans toutes les surcharges.  
  
 **✓ faire** essayez des paramètres de commande pour le rendre possible d’utiliser le mot clé params.  
  
 **✓ envisagez** en fournissant des surcharges spéciaux et les chemins de code pour les appels avec un petit nombre d’arguments dans les API très dépendantes des performances.  
  
 Cela permet d’éviter de créer des objets de tableau lors de l’API est appelée avec un petit nombre d’arguments. Les noms des paramètres du formulaire en prenant une forme au singulier du paramètre de tableau et en ajoutant un suffixe numérique.  
  
 Vous devez uniquement procéder si vous vous apprêtez à des cas spéciaux le chemin d’accès de l’ensemble du code, pas simplement créer un tableau et appelez la méthode plus générale.  
  
 **✓ faire** n’oubliez pas que la valeur null peut être passée comme argument du tableau params.  
  
 Vous devez valider que le tableau n’est pas null avant le traitement.  
  
 **X ne pas** utiliser le `varargs` méthodes en tant que les points de suspension.  
  
 Certains langages CLR, tels que C\+\+, prennent en charge une autre convention pour le passage des listes de paramètres de variable appelées `varargs` méthodes. La convention ne doit pas être utilisée dans les infrastructures, car il n’est pas conforme CLS.  
  
### Paramètres de pointeur  
 En règle générale, les pointeurs ne doivent pas apparaître dans la surface publique d’une infrastructure bien conçue du code managé. La plupart du temps, les pointeurs doivent être encapsulées. Toutefois, dans certains cas, des pointeurs sont requis pour des raisons d’interopérabilité et l’utilisation de pointeurs dans ce cas est appropriée.  
  
 **✓ faire** offrent une alternative pour les membres qui prennent un argument de pointeur, étant donné que les pointeurs ne sont pas conformes CLS.  
  
 **X éviter** effectuant l’argument coûteux, la vérification d’arguments de pointeur.  
  
 **✓ faire** respectent les conventions de pointeur associé courants lors de la conception de membres avec des pointeurs.  
  
 Par exemple, il n’est pas nécessaire de transmettre l’index de début, car l’arithmétique de pointeur simple peut être utilisé pour obtenir le même résultat.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Règles de conception de membres](../../../docs/standard/design-guidelines/member.md)   
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)