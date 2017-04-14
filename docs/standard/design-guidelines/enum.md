---
title: "Conception d’&#233;num&#233;rations | Microsoft Docs"
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
  - "conception de type, énumérations"
  - "énumérations simples"
  - "énumérations (.NET Framework), les règles de conception"
  - "indications de conception de bibliothèques de classes (.NET Framework), énumérations"
  - "énumérations d’indicateurs"
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Conception d’&#233;num&#233;rations
Énumérations sont un type spécial de type valeur. Il existe deux genres d’enums : les enums enums et indicateur simples.  
  
 Énumérations simples représentent des petits ensembles fermés de choix. Un exemple courant de l’énumération simple est un jeu de couleurs.  
  
 Énumérations d’indicateur sont conçues pour prendre en charge les opérations de bits des valeurs enum. Un exemple courant de l’énumération d’indicateurs est une liste d’options.  
  
 **✓ faire** permet une énumération de type fort aux paramètres, propriétés et de retourner des valeurs qui représentent des ensembles de valeurs.  
  
 **✓ faire** privilégient l’utilisation d’un enum au lieu de constantes statiques.  
  
 **X ne pas** utilise un enum pour les ensembles ouverts \(par exemple, la version du système d’exploitation, les noms de vos les amis, etc.\).  
  
 **X ne pas** fournir des valeurs enum réservé qui sont destinés à un usage ultérieur.  
  
 Vous pouvez toujours simplement ajouter des valeurs à l’énumération existante à un stade ultérieur. Consultez la page [Ajout de valeurs aux énumérations](#add_value) pour plus d’informations sur l’ajout de valeurs aux énumérations. Valeurs réservées simplement polluent le jeu de valeurs réelles et sont susceptibles d’entraîner des erreurs de l’utilisateur.  
  
 **X éviter** exposer publiquement des énumérations avec une seule valeur.  
  
 Une pratique courante pour assurer une extensibilité future d’API C consiste à ajouter des paramètres réservés pour les signatures de méthode. Ces paramètres réservés peuvent être exprimés sous forme d’enum avec une valeur par défaut. Non, cela doit être fait dans l’API managé. La surcharge de méthode permet d’ajouter des paramètres dans les futures versions.  
  
 **X ne pas** inclut les valeurs de sentinelle dans les énumérations.  
  
 Même s’ils sont parfois utiles aux développeurs du framework, les valeurs de sentinelle sont confus pour les utilisateurs de l’infrastructure. Ils sont utilisés pour suivre l’état de l’enum plutôt que l’une des valeurs de l’ensemble représenté par l’énumération.  
  
 **✓ faire** fournir une valeur zéro sur les énumérations simples.  
  
 La valeur, appelez quelque chose comme « None ». Si cette valeur n’est pas appropriée pour cette énumération particulier, la valeur par défaut courante pour l’énumération doit avoir la valeur sous\-jacente égale à zéro.  
  
 **✓ envisagez** à l’aide de <xref:System.Int32> \(la valeur par défaut dans la plupart des langages de programmation\) comme type sous\-jacent d’une énumération, sauf si une des opérations suivantes est vraie :  
  
-   L’énumération est une énumération d’indicateurs et vous disposez de plus de 32 ou souhaitez avoir plus dans le futur.  
  
-   Le type sous\-jacent doit être différent de celui <xref:System.Int32> pour simplifier l’interopérabilité avec du code non managé attendant des énumérations de taille différente.  
  
-   Un type sous\-jacent plus petit entraînerait des économies substantielles dans l’espace. Si vous pensez que l’enum à être utilisée principalement comme argument pour le flux de contrôle, la taille importe peu. Le gain d’espace peut être important si :  
  
    -   Vous pensez que l’enum à être utilisé en tant que champ dans une structure très fréquemment instanciée ou une classe.  
  
    -   Vous pensez que les utilisateurs à créer des grands tableaux ou collections d’instances de l’enum.  
  
    -   Vous vous attendez un grand nombre d’instances de l’énumération doit être sérialisé.  
  
 Pour une utilisation en mémoire, n’oubliez pas que les objets gérés sont toujours `DWORD`\-alignés, vous devez en fait plusieurs énumérations ou autres petites structures dans une instance à compresser une énumération avec les plus petits afin de faire la différence, car la taille d’instance total sera toujours arrondie à un `DWORD`.  
  
 **✓ faire** nom des énumérations d’indicateur avec des noms au pluriel ou expressions nominales et les énumérations simples avec des noms au singulier ou expressions nominales.  
  
 **X ne pas** étendre <xref:System.Enum?displayProperty=fullName> directement.  
  
 <xref:System.Enum?displayProperty=fullName> est un type spécial utilisé par le CLR pour créer des énumérations définies par l’utilisateur. La plupart des langages de programmation fournissent un élément de programmation qui vous permet d’accéder à cette fonctionnalité. Par exemple, en c\# le `enum` mot clé est utilisé pour définir une énumération.  
  
<a name="design"></a>   
### Conception énumérations d’indicateur  
 **✓ faire** appliquer les <xref:System.FlagsAttribute?displayProperty=fullName> aux énumérations d’indicateur. N’appliquez pas cet attribut aux énumérations simples.  
  
 **✓ faire** utiliser des puissances de deux pour les valeurs d’énumération indicateur afin qu’ils puissent être combinés librement à l’aide de l’opération OR au niveau du bit.  
  
 **✓ envisagez** fournissant les valeurs enum spécial pour couramment utilisé des combinaisons d’indicateurs.  
  
 Les opérations de bits sont un concept avancé et ne doivent pas être requises pour les tâches simples.<xref:System.IO.FileAccess> est un exemple d’une telle valeur spéciale.  
  
 **X éviter** créer des énumérations d’indicateur où certaines combinaisons de valeurs ne sont pas valides.  
  
 **X éviter** à l’aide de valeurs de l’indicateur enum de zéro, sauf si la valeur représente « tous les indicateurs sont désactivés » et est nommée de façon appropriée, comme indiqué par l’instruction suivante.  
  
 **✓ faire** nom de la valeur zéro des énumérations d’indicateur `None`. Pour une énumération d’indicateur, la valeur doit toujours signifier « tous les indicateurs sont désactivés. »  
  
<a name="add_value"></a>   
### Ajout de valeur aux énumérations  
 Il est très courant pour découvrir que vous devez ajouter des valeurs à une énumération une fois que vous l’avez déjà expédié. Il est un problème de compatibilité d’applications potentiels que lorsque la valeur nouvellement ajoutée est retournée à partir d’une API existante, car applications mal écrites peut ne pas gérer correctement la nouvelle valeur.  
  
 **✓ envisagez** Ajout de valeurs aux énumérations, en dépit d’un léger risque de compatibilité.  
  
 Si vous avez des données réelles sur les incompatibilités des applications dus à des ajouts à un enum, envisagez d’ajouter une nouvelle API qui renvoie les valeurs nouvelles et anciennes et désapprouver l’ancienne API, qui doit continuer à retourner simplement les anciennes valeurs. Cela garantit que vos applications existantes restent compatibles.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Conception de type](../../../docs/standard/design-guidelines/type.md)   
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)