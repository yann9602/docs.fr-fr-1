---
title: "Conception d'énumérations"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3ee73e8677ca3fd48f4bb3c94bd4e15c49a564c7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="enum-design"></a>Conception d'énumérations
Les énumérations sont un type spécial de type valeur. Il existe deux genres d’enums : les enums enums et indicateur simples.  
  
 Les énumérations simples représentent des petits ensembles fermés de choix. Un exemple courant de l’enum simple est un jeu de couleurs.  
  
 Les énumérations d’indicateur sont conçues pour prendre en charge les opérations de bits des valeurs enum. Un exemple courant de l’énumération d’indicateurs est une liste d’options.  
  
 **✓ FAIRE** permet un enum de type fort aux paramètres, propriétés et retourner des valeurs qui représentent les ensembles de valeurs.  
  
 **✓ FAIRE** sont favorables à l’aide d’un enum au lieu de constantes statiques.  
  
 **X ne sont pas** utiliser un enum pour les ensembles ouverts (par exemple, la version du système d’exploitation, les noms de vos amis, un etc.).  
  
 **X ne sont pas** fournissent des valeurs d’enum réservé qui sont destinés à un usage ultérieur.  
  
 Vous pouvez toujours simplement ajouter des valeurs à l’énumération existante à un stade ultérieur. Consultez [Ajout de valeurs pour les Enums](#add_value) pour plus d’informations sur l’ajout de valeurs pour les enums. Valeurs réservées simplement pollue pas l’ensemble de valeurs réelles et sont susceptibles d’entraîner des erreurs de l’utilisateur.  
  
 **X Évitez** exposer publiquement des énumérations avec une seule valeur.  
  
 Une pratique courante pour assurer une extensibilité future d’API C consiste à ajouter des paramètres réservés pour les signatures de méthode. Ces paramètres réservés peuvent être exprimées comme les enums avec une valeur par défaut. Cela ne doit pas être effectuée dans les API managées. La surcharge de méthode permet d’ajouter des paramètres dans les futures versions.  
  
 **X ne sont pas** inclure des valeurs de sentinelle dans les énumérations.  
  
 Même s’ils sont parfois utiles aux développeurs de framework, les valeurs de sentinelle sont source de confusion pour les utilisateurs de l’infrastructure. Ils sont utilisés pour suivre l’état de l’enum plutôt que d’être l’une des valeurs à partir de l’ensemble représenté par l’énumération.  
  
 **✓ FAIRE** fournir une valeur de zéro sur les énumérations simples.  
  
 La valeur, appelez quelque chose comme « None ». Si une telle valeur n’est pas appropriée pour cet enum particulier, la valeur par défaut plus courante pour l’énumération doit avoir la valeur sous-jacente égale à zéro.  
  
 **✓ Envisagez** à l’aide de <xref:System.Int32> (la valeur par défaut dans la plupart des langages de programmation) en tant que le type sous-jacent d’une énumération, sauf si une des opérations suivantes est vraie :  
  
-   L’enum est un enum et que vous disposez de plus de 32 indicateurs ou est censé avoir plus d’informations à l’avenir.  
  
-   Le type sous-jacent doit être différent de celui <xref:System.Int32> pour simplifier l’interopérabilité avec du code non managé attendu enums de taille différente.  
  
-   Un type sous-jacent plus petit entraînerait des économies substantielles en espace. Si vous pensez que l’énumération sera principalement utilisée comme argument d’un flux de contrôle, la taille importe peu. Les économies de taille peuvent être importantes si :  
  
    -   Vous vous attendez l’enum à utiliser en tant que champ dans une structure très fréquemment instanciée ou une classe.  
  
    -   Vous pensez que les utilisateurs à créer des tableaux volumineux ou des collections d’instances de l’enum.  
  
    -   Vous prévoyez un grand nombre d’instances de l’enum doit être sérialisé.  
  
 Pour l’utilisation de mémoire, gardez à l’esprit que les objets managés sont toujours `DWORD`-alignés, vous devez efficacement plusieurs énumérations ou autres structures de petite dans une instance compresser un enum plus petit avec afin de faire la différence, car la taille du nombre total d’instances est toujours continue à être arrondi à un `DWORD`.  
  
 **✓ FAIRE** nommer les énumérations d’indicateur avec des noms au pluriel ou des expressions nominales et énumérations simples avec des noms au singulier ou des expressions nominales.  
  
 **X ne sont pas** étendre <xref:System.Enum?displayProperty=nameWithType> directement.  
  
 <xref:System.Enum?displayProperty=nameWithType>est un type spécial utilisé par le CLR pour créer des énumérations de défini par l’utilisateur. La plupart des langages de programmation fournissent un élément de programmation qui vous permet d’accéder à cette fonctionnalité. Par exemple, en c# le `enum` est utilisé pour définir une énumération.  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a>Conception énumérations d’indicateur  
 **✓ FAIRE** appliquer le <xref:System.FlagsAttribute?displayProperty=nameWithType> pour les énumérations d’indicateur. N’appliquez pas cet attribut pour les énumérations simples.  
  
 **✓ FAIRE** utiliser des puissances de deux pour les valeurs d’énumération indicateur afin qu’ils peuvent être combinés librement à l’aide de l’opération OR au niveau du bit.  
  
 **✓ Envisagez** fournissant des valeurs enum spécial pour couramment utilisé les combinaisons d’indicateurs.  
  
 Opérations de bits sont un concept avancé et ne doivent pas être requises pour les tâches simples. <xref:System.IO.FileAccess.ReadWrite>est un exemple d’une telle valeur spéciale.  
  
 **X Évitez** création enums indicateur où certaines combinaisons de valeurs ne sont pas valides.  
  
 **X Évitez** à l’aide de valeurs de l’indicateur enum de zéro, sauf si la valeur représente « tous les indicateurs sont effacés » et est nommée de façon appropriée, comme indiqué par l’instruction suivante.  
  
 **✓ FAIRE** nom de la valeur zéro des énumérations d’indicateur `None`. Pour une énumération d’indicateur, la valeur doit toujours signifier « tous les indicateurs sont effacés. »  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a>L’ajout de valeur pour les Enums  
 Il est très courant pour découvrir que vous devez ajouter des valeurs à une énumération une fois que vous l’avez déjà expédié. A un problème de compatibilité d’application potentiel la valeur nouvellement ajoutée est retournée à partir d’une API existante, car des applications mal écrites peut ne pas gérer correctement la nouvelle valeur.  
  
 **✓ Envisagez** Ajout de valeurs pour les enums, en dépit d’un léger risque de compatibilité.  
  
 Si vous avez des données réelles concernant les incompatibilités application dus à des ajouts à un enum, envisagez d’ajouter une nouvelle API qui renvoie les valeurs anciennes et nouvelles et désapprouver l’ancien API, ce qui doit continuer à retourner uniquement les anciennes valeurs. Cela garantit que vos applications existantes restent compatibles.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions pour la conception des types](../../../docs/standard/design-guidelines/type.md)  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
