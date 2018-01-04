---
title: "Contexte de schéma XAML par défaut et contexte de schéma XAML WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ee7c83868934f1a524bb0068ea5e749e6cbfab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="default-xaml-schema-context-and-wpf-xaml-schema-context"></a>Contexte de schéma XAML par défaut et contexte de schéma XAML WPF
Un contexte de schéma XAML est une entité conceptuelle qui qualifie la façon dont une production XAML qui utilise un vocabulaire XAML particulier interagit avec l’objet de comportement, y compris la mappage de type est résolu, comment les assemblys sont chargés, comment certaines lecteur et writer d’écriture les paramètres sont interprétés. Cette rubrique décrit les fonctionnalités des Services XAML .NET Framework et le contexte de schéma XAML par défaut associé, qui est basé sur le système de type CLR. Cette rubrique décrit également le contexte de schéma XAML est utilisé pour WPF.  
  
## <a name="default-xaml-schema-context"></a>Contexte de schéma XAML par défaut  
 Les Services XAML .NET framework implémente et utilise un contexte de schéma XAML par défaut. Le comportement de contexte de schéma XAML par défaut n’est pas toujours complètement visible dans l’API de la <xref:System.Xaml.XamlSchemaContext> classe. Toutefois, dans de nombreux cas le comportement que le contexte de schéma XAML par défaut est observable par le biais des API courantes du système de type XAML, tels que les membres de <xref:System.Xaml.XamlMember> ou <xref:System.Xaml.XamlType>, ou via les API exposées sur les lecteurs et writers XAML qui sont à l’aide de le contexte de schéma XAML par défaut.  
  
 Vous pouvez créer un <xref:System.Xaml.XamlSchemaContext> qui encapsule le comportement par défaut en appelant le <xref:System.Xaml.XamlSchemaContext> constructeur. Cela crée explicitement le contexte de schéma XAML par défaut. Le même contexte de schéma XAML par défaut est créé implicitement, si vous initialisez un lecteur ou un writer XAML à l’aide des API qui ne prendre pas explicitement un <xref:System.Xaml.XamlSchemaContext> paramètre d’entrée.  
  
 Le contexte de schéma XAML par défaut repose sur la réflexion CLR pour son comportement de mappage de type. Cela comprend l’examen de la définition du CLR <xref:System.Type>et <xref:System.Reflection.PropertyInfo> ou <xref:System.Reflection.MethodInfo>. En outre, les attributs CLR sur les types ou membres est utilisé afin de remplir les détails pour le type XAML ou aux informations de membre XAML qui utilise le type de stockage CLR. Le contexte de schéma XAML par défaut ne nécessite pas de type système extension techniques telles que le `Invoker` de modèle, car les informations nécessaires sont disponibles à partir du système de type CLR.  
  
 Pour la logique de chargement d’un assembly, le contexte de schéma XAML par défaut s’appuie principalement sur toutes les valeurs de l’assembly fournies dans les mappages d’espace de noms XAML. En outre, <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A> peut conseiller un assembly à charger, pour des scénarios tels que le chargement des types internes.  
  
## <a name="wpf-xaml-schema-context"></a>Contexte de schéma XAML WPF  
 Le contexte de schéma XAML WPF est décrite dans cette rubrique, car l’implémentation WPF fournit une illustration intéressante des types de fonctionnalités qui peuvent être introduites en implémentant un contexte de schéma XAML par défaut. En outre, le concept de contexte de schéma XAML n’est pas traitée beaucoup dans la documentation WPF concernant XAML WPF ; le comportement permettant le contexte de schéma XAML peut uniquement être entièrement faciles à comprendre si intégré à en savoir plus sur le fonctionnement de contexte de schéma XAML par défaut. Le contexte de schéma XAML WPF implémente le comportement suivant.  
  
 **Substitutions de recherche :** WPF a quelques modèles de contenu pour le code XAML où il existe des propriétés de contenu XAML fonctionnent sans se <xref:System.Windows.Markup.ContentPropertyAttribute> avec attributs. <xref:System.Xaml.XamlType.LookupContentProperty%2A>remplacements pour WPF implémentent ce comportement.  
  
 **Report pour les expressions de WPF :** WPF comprend plusieurs classes d’expressions qui différeront d’une valeur jusqu'à ce qu’un contexte d’exécution n’est disponible. En outre, expansion de modèle est un comportement d’exécution qui s’appuie sur les techniques de report.  
  
 **Optimisations de recherche du système de type :** WPF a un étendue XAML vocabulaire et le modèle objet, notamment des définitions de membre de classe de base qui héritent des centaines de classes définies par WPF. En outre, WPF est répartie sur plusieurs assemblys. WPF optimise sa recherche de type à l’aide des tables de recherche et d’autres techniques. Cela fournit des améliorations de performances sur le contexte de schéma XAML par défaut et sa recherche de type basé sur CLR. Dans les cas où les types n’existent pas dans une table de correspondance, le comportement utilise des techniques de contexte de schéma XAML sont similaires au contexte de schéma XAML par défaut.  
  
 **Extension de XamlType et XamlMember :** WPF étend les concepts de propriétés avec les propriétés de dépendance et concepts d’événements avec des événements routés. Pour donner à ces concepts une meilleure visibilité pour les opérations de traitement XAML, WPF étend <xref:System.Xaml.XamlType> et <xref:System.Xaml.XamlMember>et ajoute les propriétés internes qui signalent la propriété de dépendance et de routage des caractéristiques de l’événement.  
  
### <a name="accessing-the-wpf-xaml-schema-context"></a>L’accès au contexte de schéma XAML WPF  
 Si vous utilisez des techniques XAML qui sont basées sur WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> ou <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>, le contexte de schéma XAML WPF est déjà en cours d’utilisation sur ces lecteur XAML et les implémentations de writer XAML.  
  
 Si vous utilisez un autre lecteur XAML ou les implémentations de writer XAML n’initialisent pas avec le contexte de schéma XAML WPF, vous pouvez être en mesure d’obtenir un contexte de schéma à partir de XAML WPF <xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=nameWithType>. Vous pouvez ensuite utiliser cette valeur en tant que l’initialisation pour les autres API qui utilisent un <xref:System.Xaml.XamlSchemaContext>. Par exemple, vous pouvez appeler <xref:System.Xaml.XamlXmlReader.%23ctor%2A> pour l’initialisation et transmettre le contexte de schéma XAML WPF. Ou bien, vous pouvez utiliser le contexte de schéma XAML WPF pour les opérations de système de type XAML. Il peut s’agir de l’initialisation de construction d’un <xref:System.Xaml.XamlType> ou <xref:System.Xaml.XamlMember>, ou en appelant <xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=nameWithType>.  
  
 Notez que si vous accédez à certains aspects de XAML WPF à partir d’un pur perspectives de flux de nœud XAML, certaines des fonctions d’infrastructure WPF ne peuvent pas avoir encore été utilisées. Par exemple, les modèles WPF pour les contrôles ne sont pas appliquées encore. Par conséquent, si vous accédez à une propriété peut être remplie avec une arborescence visuelle complète en cours d’exécution, vous verrez uniquement une valeur de propriété qui fait référence à un modèle. Le contexte de service fourni pour les extensions de balisage peut également être inexact si fournies à partir d’une situation non-runtime et peut entraîner des exceptions lors de la tentative d’écriture d’un graphique d’objet.  
  
## <a name="xaml-and-assembly-loading"></a>XAML et le chargement d’Assembly  
 Chargement d’assemblys pour XAML et les Services XAML .NET Framework s’intègre avec le concept défini par le CLR de <xref:System.AppDomain>. Un contexte de schéma XAML interprète comment charger les assemblys ou rechercher des types au moment de l’exécution ou le moment du design, en fonction de l’utilisation de <xref:System.AppDomain> et d’autres facteurs. La logique est légèrement différente selon que le code XAML est XAML libre pour un lecteur XAML, code XAML compilé dans une DLL par `XamlBuildTask`, ou BAML généré par WPF `PresentationBuildTask`.  
  
 Le contexte de schéma XAML pour WPF s’intègre avec le modèle d’application WPF, qui à son tour utilise <xref:System.AppDomain> , ainsi que d’autres facteurs sont les détails de l’implémentation WPF.  
  
#### <a name="xaml-reader-input-loose-xaml"></a>Lecteur XAML d’entrée (XAML libre)  
  
1.  Le contexte de schéma XAML parcourt le <xref:System.AppDomain> de l’application, en recherchant un assembly déjà chargé qui correspond à tous les aspects du nom, depuis le plus récemment assembly chargé. Si une correspondance est trouvée, cet assembly est utilisé pour la résolution.  
  
2.  Sinon, une des techniques suivantes basé sur CLR <xref:System.Reflection.Assembly> API sont utilisées pour charger un assembly :  
  
    -   Si le nom est qualifié dans le mappage, appelez <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> sur le nom qualifié.  
  
    -   Si l’étape précédente échoue, utilisez le nom court (et le jeton de clé publique le cas échéant) pour appeler <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
    -   Si le nom non qualifié dans le mappage, appelez <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
#### <a name="xamlbuildtask"></a>XamlBuildTask  
 `XamlBuildTask`est utilisé pour [!INCLUDE[vsindigo](../../../includes/vsindigo-md.md)] et [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)].  
  
 Notez que les références d’assembly via `XamlBuildTask` sont toujours qualifiées.  
  
1.  Appeler <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> sur le nom qualifié.  
  
2.  Si l’étape précédente échoue, utilisez le nom court (et le jeton de clé publique le cas échéant) pour appeler <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
#### <a name="baml-presentationbuildtask"></a>BAML (PresentationBuildTask)  
 Il existe deux aspects de chargement d’assemblys pour BAML : le chargement de l’assembly d’origine qui contient le code BAML en tant que composant et le chargement des assemblys de stockage de type pour tous les types référencés par la production BAML.  
  
##### <a name="assembly-load-for-initial-markup"></a>Chargement de l’assembly pour le balisage initiale :  
 La référence à l’assembly à charger le balisage d’est toujours non qualifiée.  
  
1.  Le contexte de schéma XAML WPF effectue une itération dans le <xref:System.AppDomain> de l’application WPF, en recherchant un assembly déjà chargé qui correspond à tous les aspects du nom, depuis le plus récemment assembly chargé. Si une correspondance est trouvée, cet assembly est utilisé pour la résolution.  
  
2.  Si l’étape précédente échoue, utilisez le nom court (et le jeton de clé publique le cas échéant) pour appeler <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
##### <a name="assembly-references-by-baml-types"></a>Références d’assembly par types BAML :  
 Références d’assembly pour les types utilisés dans la production BAML sont toujours complet comme sortie de la tâche de génération.  
  
1.  Le contexte de schéma XAML WPF effectue une itération dans le <xref:System.AppDomain> de l’application WPF, en recherchant un assembly déjà chargé qui correspond à tous les aspects du nom, depuis le plus récemment assembly chargé. Si une correspondance est trouvée, cet assembly est utilisé pour la résolution.  
  
2.  Sinon, une des techniques suivantes est utilisée pour charger un assembly :  
  
    -   Appeler <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> sur le nom qualifié.  
  
    -   Si un nom court + la combinaison de jeton clé publique correspond à l’assembly qui le BAML a été chargé à partir de, utilisez cet assembly.  
  
    -   Utilisez le nom court + jeton de clé publique pour appeler <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnement des concepts et structures du flux de nœud XAML](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)
