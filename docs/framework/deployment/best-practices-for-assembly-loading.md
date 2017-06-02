---
title: "Meilleures pratiques pour le chargement d&#39;assembly | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "assemblys, liaison"
  - "assemblys, charger"
  - "erreurs de chargement d'assemblys"
  - "contexte de chargement par défaut"
  - "contextes de chargement"
  - "chargement (contexte)"
  - "LoadFrom (méthode)"
  - "LoadWithPartialName (méthode)"
  - "TypeLoadException (classe), causes"
ms.assetid: 68d1c539-6a47-4614-ab59-4b071c9d4b4c
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# Meilleures pratiques pour le chargement d&#39;assembly
Cet article explique des moyens d'éviter des problèmes d'identités de type qui peuvent mener à <xref:System.InvalidCastException>, <xref:System.MissingMethodException> et à d'autres erreurs.  L'article aborde les recommandations suivantes :  
  
-   [Comprendre les avantages et les inconvénients des contextes de chargement](#load_contexts)  
  
-   [Éviter de créer des liens sur les noms d'assemblys partiels](#avoid_partial_names)  
  
-   [Éviter de charger un assembly dans plusieurs contextes](#avoid_loading_into_multiple_contexts)  
  
-   [Éviter de charger plusieurs versions d'un assembly dans le même contexte](#avoid_loading_multiple_versions)  
  
-   [Envisager de basculer vers le contexte de chargement par défaut](#switch_to_default)  
  
 La première recommandation, [Comprendre les avantages et les inconvénients des contextes de chargement](#load_contexts), fournit les informations générales pour les autres recommandations, parce qu'elles sont toutes liées à une connaissance des contextes de chargement.  
  
<a name="load_contexts"></a>   
## Comprendre les avantages et les inconvénients des contextes de chargement  
 Au sein d'un domaine d'application, les assemblys peuvent être chargés dans l'un des trois contextes, ou peuvent être chargés sans contexte :  
  
-   Le contexte de chargement par défaut contient des assemblys trouvés par le biais de la détection dans le Global Assembly Cache, dans un magasin d'assemblys de l'hôte si le runtime est hébergé \(par exemple, dans SQL Server\), et l'<xref:System.AppDomainSetup.ApplicationBase%2A> et le <xref:System.AppDomainSetup.PrivateBinPath%2A> du domaine d'application.  La plupart des surcharges de la méthode <xref:System.Reflection.Assembly.Load%2A> chargent des assemblys dans ce contexte.  
  
-   Le contexte de chargement contient des assemblys chargés à partir d'emplacements dans lesquels le chargeur n'effectue aucune recherche.  Par exemple, les compléments peuvent être installés dans un répertoire qui ne se situe pas sous le chemin d'accès d'application.  <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName>, <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=fullName> et <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=fullName> sont des exemples de méthodes qui se chargent par chemin d'accès.  
  
-   Le contexte de réflexion uniquement contient des assemblys chargés avec les méthodes <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> et <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.  Le code dans ce contexte ne peut pas être exécuté, donc il n'est pas abordé ici.  Pour plus d'informations, consultez [Comment : charger des assemblys dans le contexte de réflexion uniquement](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
-   Si vous avez généré un assembly dynamique transitoire à l'aide de l'émission de réflexion, l'assembly n'est présent dans aucun contexte.  De plus, la plupart des assemblys chargés à l'aide de la méthode <xref:System.Reflection.Assembly.LoadFile%2A> sont chargés sans contexte, et les assemblys chargés à partir des tableaux d'octets sont chargés sans contexte à moins que leur identité \(après que la stratégie a été appliquée\) établisse qu'ils sont dans le Global Assembly Cache.  
  
 Les contextes d'exécution présentent des avantages et des inconvénients, comme discuté dans les sections suivantes.  
  
### Contexte de chargement par défaut  
 Lorsque les assemblys sont chargés dans le contexte de chargement par défaut, leurs dépendances sont chargées automatiquement.  Les dépendances chargées dans le contexte de chargement par défaut sont recherchées automatiquement pour les assemblys dans le contexte de chargement ou le contexte de chargement par défaut.  Le chargement par identité d'assembly augmente la stabilité des applications en vérifiant que les versions inconnues d'assemblys ne sont pas utilisées \(consultez la section [Éviter de créer des liens sur les noms d'assemblys partiels](#avoid_partial_names) \).  
  
 L'utilisation du contexte de chargement par défaut présente les inconvénients suivants :  
  
-   Les dépendances chargées dans d'autres contextes ne sont pas disponibles.  
  
-   Vous ne pouvez pas charger d'assemblys à partir d'emplacements situés à l'extérieur du chemin d'accès de détection dans le contexte de chargement par défaut.  
  
### Contexte de chargement  
 Le contexte de chargement vous permet de charger un assembly à partir d'un chemin d'accès qui ne se situe pas sous le chemin d'accès d'application, et qui n'est par conséquent pas inclus dans la détection.  Il active des dépendances à rechercher et à charger à partir de ce chemin d'accès, parce que les informations relatives au chemin d'accès sont conservées par le contexte.  De plus, les assemblys dans ce contexte peuvent utiliser des dépendances chargées dans le contexte de chargement par défaut.  
  
 Le chargement d'assemblys à l'aide de la méthode <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName>, ou de l'une des autres méthodes qui sont chargées par le chemin d'accès, présente les inconvénients suivants :  
  
-   Si un assembly avec la même identité est déjà chargé, <xref:System.Reflection.Assembly.LoadFrom%2A> retourne l'assembly chargé même si un chemin d'accès différent a été spécifié.  
  
-   Si un assembly est chargé avec <xref:System.Reflection.Assembly.LoadFrom%2A> et qu'ultérieurement un assembly dans le contexte de chargement essaie de charger le même assembly par nom complet, la tentative de chargement échoue.  Cela peut se produire lorsqu'un assembly est désérialisé.  
  
-   Si un assembly est chargé avec <xref:System.Reflection.Assembly.LoadFrom%2A> et que le chemin d'accès de détection inclut un assembly avec la même identité mais un emplacement différent, une exception <xref:System.InvalidCastException>, <xref:System.MissingMethodException> ou un autre comportement inattendu peut se produire.  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A> exige <xref:System.Security.Permissions.FileIOPermissionAccess?displayProperty=fullName> et <xref:System.Security.Permissions.FileIOPermissionAccess?displayProperty=fullName>, ou <xref:System.Net.WebPermission>, sur le chemin d'accès spécifié.  
  
-   S'il existe une image native pour l'assembly, elle n'est pas utilisée.  
  
-   L'assembly ne peut pas être chargé indépendamment du domaine.  
  
-   Dans les versions 1.0 et 1.1 du .NET Framework, la stratégie n'est pas appliquée.  
  
### Aucun contexte  
 Le chargement sans contexte est la seule option pour les assemblys transitoires générés avec l'émission de réflexion.  Le chargement sans contexte est la seule méthode pour charger plusieurs assemblys qui ont la même identité dans un domaine d'application.  Le coût de détection est évité.  
  
 Les assemblys chargés à partir des tableaux d'octets sont chargés sans contexte à moins que l'identité de l'assembly, établi lorsque la stratégie est appliquée, corresponde à l'identité d'un assembly dans le Global Assembly Cache ; dans ce cas, l'assembly est chargé à partir du Global Assembly Cache.  
  
 Le chargement d'assemblys sans contexte présente les inconvénients suivants :  
  
-   D'autres assemblys ne peuvent pas créer de liaison avec les assemblys chargés sans contexte, à moins que vous ne gériez l'événement <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName>.  
  
-   Les dépendances ne sont pas chargées automatiquement.  Vous pouvez les précharger sans contexte, dans le contexte de chargement par défaut, ou en gérant l'événement <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName>.  
  
-   Le chargement de plusieurs assemblys avec la même identité sans contexte peut provoquer des problèmes d'identités de type semblables à ceux provoqués en chargeant des assemblys avec la même identité dans plusieurs contextes.  Consultez [Éviter de charger un assembly dans plusieurs contextes](#avoid_loading_into_multiple_contexts).  
  
-   S'il existe une image native pour l'assembly, elle n'est pas utilisée.  
  
-   L'assembly ne peut pas être chargé indépendamment du domaine.  
  
-   Dans les versions 1.0 et 1.1 du .NET Framework, la stratégie n'est pas appliquée.  
  
<a name="avoid_partial_names"></a>   
## Éviter de créer des liens sur les noms d'assemblys partiels  
 La liaison de nom partiel se produit lorsque vous spécifiez uniquement une partie du nom complet d'assembly \(<xref:System.Reflection.Assembly.FullName%2A>\) lorsque vous chargez un assembly.  Par exemple, vous pouvez appeler la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> avec uniquement le nom simple de l'assembly, en omettant la version, la culture et le jeton de clé publique.  Ou vous pouvez appeler la méthode <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>, qui appelle au préalable la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> et, si cela ne permet pas de trouver l'assembly, recherche dans le Global Assembly Cache et charge la version disponible de l'assembly la plus récente.  
  
 La liaison de nom partiel peut provoquer de nombreux problèmes, notamment les éléments suivants :  
  
-   La méthode <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName> peut charger un assembly différent avec le même nom simple.  Par exemple, deux applications peuvent installer deux assemblys complètement différents qui ont tous les deux le nom simple `GraphicsLibrary` dans le Global Assembly Cache.  
  
-   L'assembly réellement chargé peut n'est pas forcément à compatibilité descendante.  Par exemple, la non spécification de la version peut entraîner le chargement d'une version beaucoup plus récente que la version pour laquelle votre programme avait été initialement écrit.  Les modifications apportées à la version ultérieure peuvent provoquer des erreurs dans votre application.  
  
-   L'assembly réellement chargé n'est pas forcément à compatibilité ascendante.  Par exemple, vous avez pu construire et tester votre application avec la version la plus récente d'un assembly, mais la liaison partielle peut charger une version beaucoup plus ancienne qui ne comporte pas certaines fonctionnalités utilisées par votre application.  
  
-   L'installation de nouvelles applications peut arrêter des applications existantes.  Une application qui utilise la méthode <xref:System.Reflection.Assembly.LoadWithPartialName%2A> peut être arrêtée en installant une version plus récente, une version incompatible d'un assembly partagé.  
  
-   Le chargement de dépendance inattendu peut se produire.  Si vous chargez deux assemblys qui partagent une dépendance, leur chargement avec liaison partielle peut aboutir à un assembly utilisant un composant qui n'a pas été construit ou testé avec.  
  
 En raison des problèmes que cela peut provoquer, la méthode <xref:System.Reflection.Assembly.LoadWithPartialName%2A> a été marquée comme étant obsolète.  Nous vous recommandons d'utiliser à la place la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>, et de spécifier des noms complets d'assemblys.  Consultez [Comprendre les avantages et les inconvénients des contextes de chargement](#load_contexts) et [Envisager de basculer vers le contexte de chargement par défaut](#switch_to_default).  
  
 Si vous souhaitez utiliser la méthode <xref:System.Reflection.Assembly.LoadWithPartialName%2A> car elle facilite le chargement de l'assembly, sachez qu'elle génère un message d'erreur identifiant l'assembly manquant lors l'échec de votre application ce qui contribue à améliorer l'expérience utilisateur. En revanche, l'utilisation automatique d'une version inconnue de l'assembly peut entraîner un comportement imprévisible et des failles de sécurité.  
  
<a name="avoid_loading_into_multiple_contexts"></a>   
## Éviter de charger un assembly dans plusieurs contextes  
 Le chargement d'un assembly dans plusieurs contextes peut provoquer des problèmes d'identités de type.  Si le même type est chargé à partir du même assembly dans deux contextes différents, c'est comme si deux types différents du même nom avaient été chargés.  Une <xref:System.InvalidCastException> est levée si vous essayez de caster un type en un autre, avec le message ambiguë indiquant que le type `MyType` ne peut pas être casté en type `MyType`.  
  
 Par exemple, supposez que l'interface `ICommunicate` est déclarée dans un assembly nommé `Utility`, référencé par votre programme et également par les autres assemblys chargés par votre programme.  Ces autres assemblys contiennent des types qui implémentent l'interface `ICommunicate`, en permettant à votre programme de les utiliser.  
  
 Maintenant considérez ce qui arrive lorsque votre programme est exécuté.  Les assemblys référencés par votre programme sont chargés dans le contexte de chargement par défaut.  Si vous chargez un assembly cible par son identité, à l'aide de la méthode <xref:System.Reflection.Assembly.Load%2A>, il sera dans le contexte de chargement par défaut, à l'instar de ses dépendances.  Votre programme et l'assembly cible utiliseront le même assembly `Utility`.  
  
 Toutefois, supposez que vous chargez l'assembly cible par son chemin d'accès de fichier, à l'aide de la méthode <xref:System.Reflection.Assembly.LoadFile%2A>.  L'assembly est chargé sans aucun contexte, ses dépendances ne sont donc pas chargées automatiquement.  Vous pouvez avoir un gestionnaire pour l'événement <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> afin de fournir la dépendance, et il peut charger l'assembly `Utility` sans contexte à l'aide de la méthode <xref:System.Reflection.Assembly.LoadFile%2A>.  À présent, lorsque vous créez une instance d'un type qui est contenu dans l'assembly cible et que vous essayez de l'assigner à une variable de type `ICommunicate`, une <xref:System.InvalidCastException> est levée parce que l'exécution considère que les interfaces `ICommunicate` dans les deux copies de l'assembly `Utility` sont de types différents.  
  
 Il y a de nombreux autres scénarios dans lesquels un assembly peut être chargé dans plusieurs contextes.  La meilleure approche consiste à éviter des conflits en déplaçant l'assembly cible dans votre chemin d'accès d'application et en utilisant la méthode <xref:System.Reflection.Assembly.Load%2A> avec le nom complet.  L'assembly est ensuite chargé dans le contexte de chargement par défaut, et les deux assemblys utilisent le même assembly `Utility`.  
  
 Si l'assembly cible doit rester à l'extérieur de votre chemin d'accès d'application, vous pouvez utiliser la méthode <xref:System.Reflection.Assembly.LoadFrom%2A> pour le charger dans le contexte de chargement.  Si l'assembly cible a été compilé avec une référence à l'assembly `Utility` de votre application, il utilisera l'assembly `Utility` que votre application a chargé dans le contexte de chargement par défaut.  Notez que les problèmes peuvent se produire si l'assembly cible comporte une dépendance sur une copie de l'assembly `Utility` située à l'extérieur de votre chemin d'accès d'application.  Si cet assembly est chargé dans le contexte de chargement avant que votre application ne charge l'assembly `Utility`, le chargement de votre application échouera.  
  
 La section [Envisager de basculer vers le contexte de chargement par défaut](#switch_to_default) aborde des solutions alternatives à l'utilisation des chargements de chemin d'accès de fichier, telles que <xref:System.Reflection.Assembly.LoadFile%2A> et <xref:System.Reflection.Assembly.LoadFrom%2A>.  
  
<a name="avoid_loading_multiple_versions"></a>   
## Éviter de charger plusieurs versions d'un assembly dans le même contexte  
 Le chargement de plusieurs versions d'un assembly dans un contexte de chargement peut provoquer des problèmes d'identités de type.  Si le même type est chargé à partir de deux versions du même assembly, c'est comme si deux types différents du même nom avaient été chargés.  Une <xref:System.InvalidCastException> est levée si vous essayez de caster un type en un autre, avec le message ambiguë indiquant que le type `MyType` ne peut pas être casté en type `MyType`.  
  
 Par exemple, votre programme peut charger directement une version de l'assembly `Utility`, et ultérieurement, il peut charger un autre assembly qui charge une version différente de l'assembly `Utility`.  Ou une erreur de codage peut entraîner deux chemins de code différents dans votre application afin de charger des versions différentes d'un assembly.  
  
 Dans le contexte de chargement par défaut, ce problème peut se produire lorsque vous utilisez la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> et que vous spécifiez des noms complets d'assemblys qui incluent des numéros de versions différents.  Pour les assemblys chargés sans contexte, le problème peut être provoqué à l'aide de la méthode <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName> pour charger le même assembly à partir de chemins d'accès différents.  Le runtime considère deux assemblys chargés à partir de chemins d'accès différents en tant qu'assemblys différents, même si leurs identités sont les mêmes.  
  
 Outre les problèmes d'identités de type, plusieurs versions d'un assembly peuvent provoquer une <xref:System.MissingMethodException> si un type chargé à partir d'une version de l'assembly est passé au code qui attend ce type d'une version différente.  Par exemple, le code peut attendre une méthode ajoutée à la version ultérieure.  
  
 Des erreurs plus subtiles peuvent se produire si le comportement du type a changé entre les versions.  Par exemple, une méthode peut lever une exception inattendue ou retourner une valeur inattendue.  
  
 Examinez avec attention votre code pour vérifier qu'une seule version d'un assembly est chargée.  Vous pouvez utiliser la méthode <xref:System.AppDomain.GetAssemblies%2A?displayProperty=fullName> afin de déterminer les assemblys qui sont chargés à un moment donné.  
  
<a name="switch_to_default"></a>   
## Envisager de basculer vers le contexte de chargement par défaut  
 Examinez les modèles de chargement et de déploiement d'assembly de votre application.  Pouvez\-vous éliminer des assemblys chargés à partir des tableaux d'octets ?  Pouvez\-vous déplacer des assemblys dans le chemin d'accès de détection ?  Si les assemblys se trouvent dans le Global Assembly Cache ou dans le chemin d'accès de détection du domaine d'application \(autrement dit, son <xref:System.AppDomainSetup.ApplicationBase%2A> et <xref:System.AppDomainSetup.PrivateBinPath%2A>\), vous pouvez charger l'assembly par son identité.  
  
 S'il n'est pas possible de placer tous vos assemblys dans le chemin d'accès de détection, envisagez des solutions alternatives telles que l'utilisation du modèle de complément interne du .NET Framework, le placement d'assemblys dans le Global Assembly Cache, ou la création de domaines d'application.  
  
### Envisager d'utiliser le modèle de complément interne du .NET Framework  
 Si vous utilisez le contexte de chargement pour implémenter des compléments, qui ne sont généralement pas installés dans la base de l'application, utilisez le modèle de complément interne du .NET Framework.  Ce modèle fournit l'isolement au niveau du domaine d'application ou du processus, sans vous obliger à gérer des domaines d'application vous\-même.  Pour plus d'informations sur le modèle de complément, consultez [Compléments et extensibilité](../../../ml/index.xml).  
  
### Envisager d'utiliser le Global Assembly Cache  
 Placez des assemblys dans le Global Assembly Cache pour bénéficier d'un chemin d'accès d'assembly partagé situé à l'extérieur de la base de l'application, sans perdre les avantages du contexte de chargement par défaut ou hériter des inconvénients des autres contextes.  
  
### Envisager d'utiliser les domaines d'application  
 Si vous déterminez que certains de vos assemblys ne peuvent pas être déployés dans le chemin d'accès de détection de l'application, envisagez de créer un domaine d'application pour ces assemblys.  Utilisez un <xref:System.AppDomainSetup> pour créer le nouveau domaine d'application et utilisez la propriété <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=fullName> pour spécifier le chemin d'accès qui contient les assemblys que vous souhaitez charger.  Si vous avez plusieurs répertoires à détecter, vous pouvez affecter à l'<xref:System.AppDomainSetup.ApplicationBase%2A> la valeur d'un répertoire racine et utiliser la propriété <xref:System.AppDomainSetup.PrivateBinPath%2A?displayProperty=fullName> pour identifier les sous\-répertoires à détecter.  Ou bien, vous pouvez créer plusieurs domaines d'application et affecter à l'<xref:System.AppDomainSetup.ApplicationBase%2A> de chaque domaine d'application la valeur du chemin d'accès approprié pour ses assemblys.  
  
 Notez que vous pouvez utiliser la méthode <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName> pour charger ces assemblys.  Étant donné qu'ils sont maintenant dans le chemin d'accès de détection, au lieu d'être chargés dans le contexte de chargement, ils seront chargés dans le contexte de chargement par défaut.  Toutefois, nous vous recommandons de basculer vers la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> et de fournir des noms complets d'assemblys afin de garantir que les versions correctes sont toujours utilisées.  
  
## Voir aussi  
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>   
 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName>   
 <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName>   
 <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName>   
 [Compléments et extensibilité](../../../ml/index.xml)