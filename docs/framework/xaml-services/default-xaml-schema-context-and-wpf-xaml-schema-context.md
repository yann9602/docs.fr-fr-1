---
title: "Default XAML Schema Context and WPF XAML Schema Context | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
caps.latest.revision: 7
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 7
---
# Default XAML Schema Context and WPF XAML Schema Context
Un contexte de schéma XAML est une entité conceptuelle qui définit la façon dont une production XAML qui utilise un vocabulaire XAML spécifique interagit avec le comportement d'écriture d'objet, notamment la façon dont le mappage de type est résolu, la façon dont les assemblys sont chargés, et la façon dont certains paramètres de lecteur et de writer sont interprétés.  Cette rubrique décrit les fonctionnalités des services XAML .NET Framework et le contexte de schéma XAML par défaut associé, en fonction du système de type CLR.  Cette rubrique décrit également le contexte de schéma XAML utilisé pour WPF.  
  
## Contexte de schéma XAML par défaut  
 Les services XAML .NET Framework implémente et utilise un contexte de schéma XAML par défaut.  Le comportement du contexte de schéma XAML par défaut n'est pas toujours entièrement visible dans l'API de la classe <xref:System.Xaml.XamlSchemaContext>.  Toutefois, dans de nombreux cas, le comportement influencé par le contexte de schéma XAML par défaut est observable dans l'API commune du système de type XAML, par exemple les membres de <xref:System.Xaml.XamlMember> ou <xref:System.Xaml.XamlType>, ou dans les API exposés dans les lecteurs et writers XAML qui utilisent le contexte de schéma XAML par défaut.  
  
 Vous pouvez créer un <xref:System.Xaml.XamlSchemaContext> qui encapsule le comportement par défaut en appelant le constructeur <xref:System.Xaml.XamlSchemaContext>.  Cette opération crée explicitement le contexte de schéma XAML par défaut.  Le même contexte de schéma XAML par défaut est créé implicitement, si vous initialisez un lecteur ou un writer XAML à l'aide d'API qui n'acceptent pas explicitement un paramètre d'entrée <xref:System.Xaml.XamlSchemaContext>.  
  
 Le contexte de schéma XAML par défaut repose sur la réflexion CLR pour le comportement du mappage de type.  Cela comprend l'analyse du CLR <xref:System.Type> de définition et de l'élément <xref:System.Reflection.PropertyInfo> ou <xref:System.Reflection.MethodInfo> associé.  En outre, les attributs CLR sur les types ou les membres permettent de spécifier les détails pour les informations de type ou membre XAML qui utilisent le type de stockage CLR.  Le contexte de schéma XAML par défaut ne requiert aucune technique d'extension du système de type telle que le modèle `Invoker`, car les informations nécessaires sont fournies par le système de type CLR.  
  
 Pour la logique de chargement d'assembly, le contexte de schéma XAML par défaut repose essentiellement sur des valeurs d'assembly fournies dans les mappages d'espace de noms XAML.  En outre, <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A> peut conseiller un assembly à charger, pour des scénarios tels que des chargements de types internes.  
  
## Contexte de schéma XAML WPF  
 Le contexte de schéma XAML WPF est décrit dans cette rubrique, car l'implémentation WPF fournit une illustration intéressante des genres de fonctionnalités pouvant être introduites en implémentant un contexte de schéma XAML autre que le contexte par défaut.  Par ailleurs, le concept de contexte de schéma XAML n'est pas beaucoup abordé dans la documentation WPF concernant XAML WPF ; le comportement activé par le contexte de schéma XAML ne peut être compris dans son ensemble que s'il est intégré à une discussion sur la façon dont le contexte de schéma XAML par défaut s'exécute.  Le contexte de schéma XAML WPF implémente le comportement suivant.  
  
 **Substitutions de recherche :** WPF présente quelques modèles de contenu pour XAML dont certaines propriétés de contenu XAML fonctionnent sans se voir attribuer <xref:System.Windows.Markup.ContentPropertyAttribute>.  Les substitutions <xref:System.Xaml.XamlType.LookupContentProperty%2A> pour WPF implémentent ce comportement.  
  
 **Différé pour les expressions WPF :** WPF présente plusieurs classes d'expressions qui diffèrent une valeur jusqu'à ce qu'un contexte d'exécution soit disponible.  En outre, l'expansion de modèle est un comportement au moment de l'exécution qui repose sur les techniques de différé.  
  
 **Optimisations de recherche du système de type :** WPF a un modèle de vocabulaire et d'objet XAML étendu, qui comprend notamment des définitions de membres de classe de base qui sont transmises par héritage à des centaines de classes définies par WPF.  En outre, WPF s'étend lui\-même à plusieurs assemblys.  WPF optimise sa recherche de type à l'aide de tables de recherche et autres techniques.  Le contexte de schéma XAML par défaut et sa recherche de type basée sur le CLR bénéficient ainsi de meilleures performances.  Si des types n'existent pas dans une table de recherche, le comportement utilise des techniques de contexte de schéma XAML qui sont semblables au contexte de schéma XAML par défaut.  
  
 **Extension de XamlType et XamlMember :** WPF étend les concepts de propriétés avec des propriétés de dépendance, et les concepts d'événements avec des événements routés.  Pour donner à ces concepts une meilleure visibilité des opérations de traitement XAML, WPF étend <xref:System.Xaml.XamlType> et <xref:System.Xaml.XamlMember>, ajoute les propriétés internes qui signalent la propriété de dépendance et les caractéristiques d'événements routés.  
  
### Accès au contexte de schéma XAML WPF  
 Si vous utilisez des techniques XAML sur <xref:System.Windows.Markup.XamlReader?displayProperty=fullName> ou <xref:System.Windows.Markup.XamlWriter?displayProperty=fullName> de WPF, le contexte de schéma XAML WPF est déjà utilisé sur ces implémentations de lecteur et writer XAML.  
  
 Si vous utilisez d'autres implémentations de lecteur ou writer XAML qui ne s'initialisent pas avec le contexte de schéma XAML WPF, vous pouvez être en mesure d'obtenir un contexte de schéma XAML WPF de production auprès de <xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=fullName>.  Vous pouvez ensuite utiliser cette valeur pour initialiser d'autres API qui utilisent un élément <xref:System.Xaml.XamlSchemaContext> Par exemple, vous pouvez appeler <xref:System.Xaml.XamlXmlReader.%23ctor%2A> pour l'initialisation et transmettre le contexte de schéma XAML WPF.  Vous pouvez également utiliser le contexte de schéma XAML WPF pour les opérations de système de type XAML.  Cela peut comprendre l'initialisation de la construction d'un élément <xref:System.Xaml.XamlType> ou<xref:System.Xaml.XamlMember> ou l'appel de <xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=fullName>.  
  
 Notez que si vous accédez à certains aspects de XAML WPF à partir de perspectives pures de flux de nœud XAML, certaines des fonctions d'infrastructure WPF peuvent ne pas avoir encore été utilisées.  Par exemple, les modèles WPF pour les contrôles ne sont pas encore appliqués.  Par conséquent, si vous accédez à une propriété qui pendant l'exécution peut être remplie avec une arborescence d'éléments visuels complète, il se peut que seule une valeur de propriété faisant référence à un modèle s'affiche.  Le contexte de service fourni pour les extensions de balisage WPF peut également ne pas être correct s'il est fourni dans une situation hors exécution, et peut entraîner des exceptions lors de tentative d'écriture d'un graphique d'objets.  
  
## XAML et chargement des assemblys  
 Le chargement d'assemblys pour les services de XAML et XAML .NET Framework s'intègre avec le concept CLR de <xref:System.AppDomain>.  Un contexte de schéma XAML interprète comment charger les assemblys ou rechercher les types au moment de l'exécution ou du design, en fonction de l'utilisation de <xref:System.AppDomain> et d'autres facteurs.  La logique est légèrement différent selon que le code XAML est XAML libre pour un lecteur XAML, est du code XAML compilé dans une DLL par `XamlBuildTask`, ou est du code BAML généré par `PresentationBuildTask` de WPF.  
  
 Le contexte de schéma XAML pour WPF s'intègre avec le modèle d'application WPF, qui ensuite utilise <xref:System.AppDomain> ainsi que d'autres facteurs, détails d'implémentation WPF.  
  
#### Entrée de lecteur XAML \(XAML libre\)  
  
1.  Le contexte de schéma XAML effectue une itération au sein de <xref:System.AppDomain> de l'application, en recherchant un assembly déjà chargé qui correspond à tous les aspects du nom, en commençant par l'assembly le plus récemment chargé.  Si une correspondance est trouvée, cet assembly est utilisé pour la résolution.  
  
2.  Sinon, l'une des techniques suivantes basées sur l'API <xref:System.Reflection.Assembly> du CLR est utilisée pour charger un assembly :  
  
    -   Si le nom est qualifié dans le mappage, appelez <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName> sur le nom qualifié.  
  
    -   En cas d'échec de l'étape précédente, utilisez le nom court \(et le jeton de clé publique le cas échéant\) pour appeler <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName>.  
  
    -   Si le nom n'est pas qualifié dans le mappage, appelez <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>.  
  
#### XamlBuildTask  
 `XamlBuildTask` utilisé pour [!INCLUDE[vsindigo](../../../includes/vsindigo-md.md)] et [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)].  
  
 Notez que les références d'assembly via `XamlBuildTask` sont toujours qualifiées complètes.  
  
1.  Appelez <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName> sur le nom qualifié.  
  
2.  En cas d'échec de l'étape précédente, utilisez le nom court \(et le jeton de clé publique le cas échéant\) pour appeler <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName>.  
  
#### BAML \(PresentationBuildTask\)  
 Il existe deux aspects liés au chargement d'assemblys pour BAML : le chargement de l'assembly d'origine qui contient le code BAML en tant que composant, et le chargement des assemblys de stockage de type pour tous les types référencés par la production BAML.  
  
##### Chargement de l'assembly pour le balisage d'origine :  
 La référence à l'assembly à partir duquel le balisage doit être chargé est toujours non qualifiée.  
  
1.  Le contexte de schéma XAML WPF effectue une itération au sein de <xref:System.AppDomain> de l'application WPF, en recherchant un assembly déjà chargé qui correspond à tous les aspects du nom, en commençant par l'assembly le plus récemment chargé.  Si une correspondance est trouvée, cet assembly est utilisé pour la résolution.  
  
2.  En cas d'échec de l'étape précédente, utilisez le nom court \(et le jeton de clé publique le cas échéant\) pour appeler <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName>.  
  
##### Références d'assembly par types BAML :  
 Les références d'assembly pour les types utilisés dans la production BAML sont toujours qualifiées complètes, comme résultat de la tâche de génération.  
  
1.  Le contexte de schéma XAML WPF effectue une itération au sein de <xref:System.AppDomain> de l'application WPF, en recherchant un assembly déjà chargé qui correspond à tous les aspects du nom, en commençant par l'assembly le plus récemment chargé.  Si une correspondance est trouvée, cet assembly est utilisé pour la résolution.  
  
2.  Sinon, l'une des techniques suivantes est utilisée pour charger un assembly :  
  
    -   Appelez <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName> sur le nom qualifié.  
  
    -   Si une combinaison de nom court et jeton de clé publique correspond l'assembly à partir duquel le BAML a été chargé, utilisez cet assembly.  
  
    -   Utilisez la combinaison nom court \+ jeton de clé publique pour appeler <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName>.  
  
## Voir aussi  
 [Understanding XAML Node Stream Structures and Concepts](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)