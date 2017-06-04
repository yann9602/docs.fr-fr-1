---
title: "Diagnostics de compatibilit&#233; .NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e481270-b62a-4cb4-8dda-5b4c5b59d61d
caps.latest.revision: 7
author: "twsouthwick"
ms.author: "tasou"
manager: "wpickett"
caps.handback.revision: 7
---
# Diagnostics de compatibilit&#233; .NET
Les Diagnostics de compatibilité .NET sont des analyseurs de puissance Roslyn qui permettent d’identifier les problèmes de compatibilité entre les versions du .NET Framework. Cette liste contient tous les analyseurs disponibles, bien que seul un sous-ensemble s’applique à toute migration spécifique. Les analyseurs déterminera les problèmes qui sont applicables pour la migration planifiée et celles affichera uniquement. Pour les problèmes de diviser par les versions affectées, consultez : [la compatibilité des applications](../../../docs/framework/migration-guide/application-compatibility.md).  
  
 Chaque problème contient les informations suivantes :  
  
-   La description de ce qui a changé d’une version précédente.  
  
-   La suggestion est une description de la façon dont la modification affecte les clients et si aucune solution de contournement est disponibles pour préserver la compatibilité entre les versions.  
  
-   Une évaluation de l’importance de la modification est. Problème de compatibilité d’application sont classés comme suit :  
  
    |||  
    |-|-|  
    |Majeur|Une modification importante qui affecte un grand nombre d’applications ou nécessite une modification importante de code.|  
    |Secondaire|Une modification qui affecte un petit nombre d’applications ou qui nécessite peu de modifications de code.|  
    |Cas limite|Une modification qui affecte des applications dans des scénarios spécifiques très rares.|  
    |Transparent|Une modification avec aucune incidence sur le développeur ou l’utilisateur de l’application.|  
  
-   Version indique lorsque la modification s’affiche d’abord dans le framework. Certaines modifications sont annulées et qui est également indiqué.  
  
-   Le type de modification :  
  
    |||  
    |-|-|  
    |Reciblage|La modification affecte les applications qui sont recompilées pour cibler une nouvelle version du .NET Framework.|  
    |Exécution|La modification affecte une application existante qui cible une version antérieure du .NET Framework mais s’exécute sur une version ultérieure.|  
  
-   Les API affectés, le cas échéant.  
  
-   Les ID des tests de diagnostic disponibles  
  
<a name="diagnostic1"></a>   
## <a name="1-soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>1 : SoapFormatter Impossible de désérialiser la table de hachage et classés comme des objets de collection  
  
|||  
|-|-|  
|Détails|SoapFormatter ne garantit pas que les objets sérialisés sous un seul .NET Framework version désérialisera correctement sous une version différente. Plus précisément, certaines collections ordonnées (telles que la table de hachage) ajoutés membres entre 4.0 et 4.5 tels que les objets de ces types ne peut pas désérialiser avec .NET 4.0 si elles ont été serialzied avec le .NET 4.5. Notez que si les données sérialisées sont sérialisées et désérialisées avec la même version du .NET Framework, aucun problème se produira.|  
|Suggestion|SoapFormatter sérialisation doit être remplacée par la sérialisation de BinaryFormatter ou NetDataContractSerialization pour qu’elles soient résistantes aux modifications de .NET Framework.|  
|Portée|Secondaire|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize%28System.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize%28System.IO.Stream%2CSystem.Runtime.Remoting.Messaging.HeaderHandler%29?displayProperty=fullName><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize%28System.IO.Stream%2CSystem.Object%29?displayProperty=fullName><br /><br /> [SoapFormatter.Serialize (en-tête de flux, objet,\<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize%28System.IO.Stream%2CSystem.Object%2CSystem.Runtime.Remoting.Messaging.Header%5B%5D%29?displayProperty=fullName>|  
|Analyseurs|CD0001B<br /><br /> CD0001A|  
  
<a name="diagnostic3"></a>   
## <a name="3-wpf-datatemplate-elements-are-now-visible-to-uia"></a>3 : éléments DataTemplate WPF sont désormais visibles par UIA  
  
|||  
|-|-|  
|Détails|Auparavant, les éléments DataTemplate étaient invisibles pour l’Automation d’interface utilisateur. À compter de 4.5, UI Automation détecte ces éléments. Cela est utile dans de nombreux cas, mais peut interrompre les tests qui dépendent des arborescences UIA ne contenant ne pas les éléments DataTemplate.|  
|Suggestion|Tests de l’interface utilisateur Auomation pour cette application peut nécessiter une mise à jour pour tenir compte de l’arborescence UIA inclut des éléments DataTemplate précédemment invisibles. Par exemple, les tests qui attendent d’être contiguës de certains éléments doive maintenant attendent des éléments UIA précédemment invisibles entre les deux. Ou les tests qui reposent sur certains nombres ou des index pour les éléments UIA peuvent nécessiter une mise à jour avec de nouvelles valeurs.|  
|Portée|Bord|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Windows.DataTemplate.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Windows.DataTemplate.%23ctor%28System.Object%29?displayProperty=fullName>|  
|Analyseurs|CD0003|  
  
<a name="diagnostic4"></a>   
## <a name="4-wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>4 : texte de la zone de texte WPF sélectionnée s’affiche une couleur différente lorsque la zone de texte est inactive  
  
|||  
|-|-|  
|Détails|Dans le .NET 4.5, lorsqu’un contrôle de zone de texte WPF est inactif (il n’inclut pas le focus), le texte sélectionné dans la zone s’affiche une couleur différente de celle utilisée lorsque le contrôle est actif.|  
|Suggestion|Comportement (.NET 4.0) précédent peut être restauré en affectant la [FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported](https://msdn.microsoft.com/en-us/library/system.windows.frameworkcompatibilitypreferences.areinactiveselectionhighlightbrushkeyssupported\(v=vs.110\).aspx) propriété sur false.|  
|Portée|Bord|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Windows.Controls.TextBox?displayProperty=fullName>|  
|Analyseurs|CD0004|  
  
<a name="diagnostic5"></a>   
## <a name="5-listtforeach-can-throw-exception-when-modifying-list-item"></a>5: List<>\>. ForEach peut lever des exceptions lorsque vous modifiez l’élément de liste  
  
|||  
|-|-|  
|Détails|À compter de .NET 4.5, un `List<T>.ForEach` énumérateur lève une exception InvalidOperationException si un élément dans la collection en appelant est modifié. Auparavant, il ne lève pas d’exception mais peut entraîner des conditions de concurrence.|  
|Suggestion|Dans l’idéal, le code doit être corrigé de ne pas modifier les listes pendant l’énumération de leurs éléments qui n’est jamais une opération sûre. Pour rétablir le comportement précédent, cependant, une application peut cibler .NET 4.0.|  
|Portée|Bord|  
|Version|4.5|  
|Type|Reciblage|  
|API affectés|<xref:System.Collections.Generic.List%601.ForEach%28System.Action%7B%600%7D%29?displayProperty=fullName>|  
|Analyseurs|CD0005|  
  
<a name="diagnostic6"></a>   
## <a name="6-systemuri-parsing-adheres-to-rfc-3987"></a>6 : analyse System.Uri respecte la norme RFC 3987  
  
|||  
|-|-|  
|Détails|Analyse de l’URI a changé de différentes manières dans .NET 4.5. Notez, cependant, que ces modifications affectent uniquement des codes ciblant le .NET 4.5. Si une cible binaire .NET 4.0, l’ancien comportement est appliqué. Modifications à l’analyse des URI dans .NET 4.5 :<br /><br /> Analyse URI effectuera la normalisation et la vérification des caractères selon les dernières règles IRI de RFC 3987<br /><br /> Formulaire de normalisation Unicode C ne se fera que sur la partie hôte de l’URI<br /><br /> Mailto non valide : URI maintenant provoque une exception<br /><br /> Points de fin à la fin d’un segment de chemin d’accès sont désormais conservés<br /><br /> `file://`URI ne puissent se soustraire la `?` caractère<br /><br /> Caractères de contrôle Unicode `U+0080` via `U+009F` ne sont pas pris en charge<br /><br /> Virgule `,` ou `%2c` ne sont pas automatiquement sans séquence d’échappement|  
|Suggestion|Si la sémantique de l’analyse de .NET 4.0 URI ancien est nécessaire (souvent ne sont pas), ils peuvent être utilisés en ciblant .NET 4.0. Pour cela, à l’aide d’un TargetFrameworkAttribute sur l’assembly, ou via le système de projet de Visual Studio l’interface utilisateur dans la page de propriétés du projet.|  
|Portée|Majeur|  
|Version|4.5|  
|Type|Reciblage|  
|API affectés|<xref:System.Uri.%23ctor%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.Uri%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.String%2CSystem.UriKind%2CSystem.Uri%40%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.Uri%2CSystem.String%2CSystem.Uri%40%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.Uri%2CSystem.Uri%2CSystem.Uri%40%29?displayProperty=fullName>|  
|Analyseurs|CD0006D<br /><br /> CD0006C<br /><br /> CD0006F<br /><br /> CD0006E<br /><br /> CD0006A<br /><br /> CD0006G<br /><br /> CD0006B|  
  
<a name="diagnostic10"></a>   
## <a name="10-systemuri-escaping-now-supports-rfc-3986-httptoolsietforghtmlrfc3986"></a>10 : System.Uri échappement prend désormais en charge la norme RFC 3986 (http://tools.ietf.org/html/rfc3986)  
  
|||  
|-|-|  
|Détails|Échappement d’URI a changé dans .NET 4.5 pour prendre en charge [RFC 3986](http://tools.ietf.org/html/rfc3986). Modifications spécifiques :<br /><br /> `EscapeDataString` représente une séquence d'échappement pour les caractères réservés basés sur la norme RFC 3986.<br /><br /> `EscapeUriString` ne représente pas une séquence d'échappement pour les caractères réservés.<br /><br /> `UnescapeDataString` ne lève pas d'exception s'il rencontre une séquence d'échappement non valide.<br /><br /> Les caractères d'échappement non réservés sont sans séquence d'échappement.|  
|Suggestion|Mettre à jour les applications ne peuvent ne pas compter sur UnescapeDataString levée dans le cas d’une séquence d’échappement non valide. Ces séquences doivent être détectés directement maintenant.<br /><br /> De même, attendez que les chaînes Escaped et URI sans séquence d’échappement et les données peuvent varier à partir de .NET 4.0 et 4.5 de .NET et ne doivent pas être comparées entre les versions de .NET directement. Au lieu de cela, ils doivent être analysées et normalisés en une seule version de .NET avant que toutes les comparaisons sont effectuées.|  
|Portée|Secondaire|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Uri.EscapeDataString%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.EscapeUriString%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.UnescapeDataString%28System.String%29?displayProperty=fullName>|  
|Analyseurs|CD0010A<br /><br /> CD0010B<br /><br /> CD0010C|  
  
<a name="diagnostic11"></a>   
## <a name="11-systemnetpeertopeercollaboration-unavailable-on-windows-8"></a>11 : System.Net.PeerToPeer.Collaboration indisponible sur Windows 8  
  
|||  
|-|-|  
|Détails|L’espace de noms System.Net.PeerToPeer.Collaboration n’est pas disponible sur Windows 8 ou version ultérieure.|  
|Suggestion|Applications qui prennent en charge de Windows 8 ou ci-dessus doivent être mis à jour pour qu’elle ne dépende pas de cet espace de noms ou de ses membres.|  
|Portée|Majeur|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Net.PeerToPeer.Collaboration?displayProperty=fullName>|  
|Analyseurs|CD0011|  
  
<a name="diagnostic12"></a>   
## <a name="12-mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>12 : catalogues MEF implémentent IEnumerable et par conséquent ne peut plus être utilisés pour créer un sérialiseur  
  
|||  
|-|-|  
|Détails|À compter de .NET Framework 4.5, catalogues MEF implémentent IEnumerable et par conséquent ne peuvent plus être utilisés pour créer un sérialiseur (objet XmlSerializer). La tentative de sérialisation d'un catalogue MEF lève une exception.|  
|Suggestion|Peut ne plus utiliser MEF pour créer un sérialiseur|  
|Portée|Majeur|  
|Version|4.5|  
|Type|Exécution|  
|Analyseurs|CD0012|  
  
<a name="diagnostic13"></a>   
## <a name="13-missing-target-framework-moniker-results-in-40-behavior"></a>13 : Moniker du Framework cible manquante entraîne un comportement 4.0  
  
|||  
|-|-|  
|Détails|Applications sans un [TargetFrameworkAttribute](https://msdn.microsoft.com/en-us/library/system.runtime.versioning.targetframeworkattribute\(v=vs.110\).aspx) appliqué à l’assembly au niveau exécuteront automatiquement à l’aide de la sémantique (quirks) de .NET Framework 4.0. Pour garantir une haute qualité, il est recommandé que tous les fichiers binaires être explicitement attribué avec un TargetFrameworkAttribute indiquant la version du .NET Framework, elles ont été créées avec. Notez qu’à l’aide d’un moniker du framework cible dans un fichier de projet seront caues MSBuild pour appliquer automatiquement un TargetFrameworkAttribute.|  
|Suggestion|A [d’attribut target framework](https://msdn.microsoft.com/en-us/library/system.runtime.versioning.targetframeworkattribute\(v=vs.110\).aspx) doit être fournie, soit via l’ajout de l’attribut directement à l’assembly ou en spécifiant une infrastructure cible dans le [fichier de projet ou par le biais de Visual Studio GUI de propriétés de projet](http://blogs.msdn.com/b/visualstudio/archive/2010/05/19/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework.aspx).|  
|Portée|Majeur|  
|Version|4.5|  
|Type|Exécution|  
|Analyseurs|CD0013|  
  
<a name="diagnostic14"></a>   
## <a name="14-no-longer-able-to-set-enableviewstatemac-to-false"></a>14 : ne sont plus en mesure de définir EnableViewStateMac sur false  
  
|||  
|-|-|  
|Détails|ASP.NET ne permet plus aux développeurs de spécifier `<pages enableViewStateMac="false"/>` ou `<@Page EnableViewStateMac="false" %>`. Le code d'authentification de message (code MAC) de l'état d'affichage est à présent appliqué à toutes les demandes avec état d'affichage intégré. Seules les applications qui définir explicitement la propriété EnableViewStateMac sur false sont affectées.|  
|Suggestion|EnableViewStateMac doive être considérées comme true, et toute erreur MAC résultante doit être résolu (comme expliqué dans [cela](https://support.microsoft.com/en-us/kb/2915218) conseils, qui contient plusieurs résolutions selon les spécificités de ce qui provoque des erreurs de MAC).|  
|Portée|Majeur|  
|Version|4.5.2|  
|Type|Exécution|  
|Analyseurs|CD0014|  
  
<a name="diagnostic18"></a>   
## <a name="18-blockingcollectionttrytakefromany-does-not-throw-anymore"></a>18 : BlockingCollection<>\>. TryTakeFromAny ne lève pas d’exception plus  
  
|||  
|-|-|  
|Détails|Si l’une des collections d’entrée est marquée comme terminée, `BlockingCollection<T>.TryTakeFromAny(BlockingCollection<T>[], T)` n’est plus retourne -1 et `BlockingCollection<T>.TakeFromAny` ne lève plus une exception. Cette modification permet d'utiliser des collections lorsque l'une est vide ou terminée, alors que l'autre comporte toujours des éléments pouvant être récupérés.|  
|Suggestion|Si TryTakeFromAny retourne -1 ou lever TakeFromAny ont été utilisé pour flux de contrôle en cas d’une collection de blocage en cours terminée, ce code doit être modifié pour utiliser `.Any(b => b.IsCompleted)` pour détecter cette condition.|  
|Portée|Secondaire|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|[BlockingCollection<>\>. TakeFromAny (BlockingCollection<>\>\<xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%29?displayProperty=fullName><br /><br /> [BlockingCollection<>\>. TakeFromAny (BlockingCollection<>\>\<xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> [BlockingCollection<>\>. TryTakeFromAny (BlockingCollection<>\>\<xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%29?displayProperty=fullName><br /><br /> [BlockingCollection<>\>. TryTakeFromAny (BlockingCollection<>\>\<xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.Int32%29?displayProperty=fullName><br /><br /> [BlockingCollection<>\>. TryTakeFromAny (BlockingCollection<>\>\<xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.TimeSpan%29?displayProperty=fullName>|  
|Analyseurs|CD0018A<br /><br /> CD0018B|  
  
<a name="diagnostic19"></a>   
## <a name="19-xmlschemaexception-now-sets-line-positions-properly"></a>19 : XmlSchemaException maintenant jeux correctement des positions de ligne  
  
|||  
|-|-|  
|Détails|Si la valeur LoadOptions.SetLineInfo est passée à la méthode Load et une erreur de validation se produit, les propriétés XmlSchemaException.LineNumber et XmlSchemaException.LinePosition contiennent désormais des informations de ligne.|  
|Suggestion|Code de gestion des exceptions qui suppose que XmlSchemaException.LineNumber et XmlSchemaException.LinePosition ne sera pas ensemble doit être mis à jour, car ces propriétés seront maintenant définies correctement lorsque SetLineInfo est utilisé lors du chargement XML.|  
|Portée|Bord|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Xml.Linq.LoadOptions?displayProperty=fullName>|  
|Analyseurs|CD0019|  
  
<a name="diagnostic20"></a>   
## <a name="20-systemactivities-is-now-aptca"></a>20 : System.Activities est désormais APTCA  
  
|||  
|-|-|  
|Détails|L’assembly est marqué avec l’attribut AllowPartiallyTrustedCallersAttribute.|  
|Suggestion|Les classes dérivées ne peuvent pas être marqués avec l’attribut SecurityCriticalAttribute. Auparavant, les types dérivés devaient être marqués avec l’attribut SecurityCriticalAttribute. Toutefois, cette modification ne doit pas avoir d'impact réel.|  
|Portée|Bord|  
|Version|4.5|  
|Type|Exécution|  
|Analyseurs|CD0020|  
  
<a name="diagnostic21"></a>   
## <a name="21-workflow-30-types-are-obsolete"></a>21 : types de workFlow 3.0 sont obsolètes  
  
|||  
|-|-|  
|Détails|API de Windows Workflow Foundation (WWF) 3.0 (ceux de l’espace de noms System.Workflow) est désormais obsolètes.|  
|Suggestion|Nouvelles API de 4.0 de WWF (dans System.Activities) doivent être utilisées à la place. Un exemple d’utilisation des nouvelles API sont accessibles [ici](https://msdn.microsoft.com/en-us/library/jj205427.aspx) et autres conseils sont disponibles [ici](http://blogs.msdn.com/b/workflowteam/archive/2012/02/08/deprecatingwf3.aspx). Également, dans la mesure où les API de 3.0 WWF sont toujours pris en charge, ils peuvent être utilisés et l’avertissement au moment de la génération évitées également la supprimer ou à l’aide d’un compilateur antérieur.|  
|Portée|Majeur|  
|Version|4.5|  
|Type|Reciblage|  
|Analyseurs|CD0021|  
  
<a name="diagnostic22"></a>   
## <a name="22-some-workflow-drag-and-drop-apis-are-obsolete"></a>22 : certains flux de travail glisser -déplacer API sont obsolètes  
  
|||  
|-|-|  
|Détails|Cette API de glisser-déplacer de flux de travail est obsolète et génèrent des avertissements de compilateur si l’application est régénérée contre 4.5.|  
|Suggestion|Nouvelle [DragDropHelper](https://msdn.microsoft.com/en-us/library/system.activities.presentation.dragdrophelper\(v=vs.110\).aspx) API qui prennent en charge les opérations avec plusieurs objets doivent être utilisées à la place. Vous pouvez également les avertissements de build peuvent être supprimés ou ils peuvent être évités à l’aide d’un compilateur antérieur. Les API sont toujours pris en charge.|  
|Portée|Secondaire|  
|Version|4.5|  
|Type|Reciblage|  
|API affectés|<xref:System.Activities.Presentation.DragDropHelper.DoDragMove%28System.Activities.Presentation.WorkflowViewElement%2CSystem.Windows.Point%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView%28System.Windows.DragEventArgs%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem%28System.Windows.DragEventArgs%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject%28System.Windows.DependencyObject%2CSystem.Windows.DragEventArgs%2CSystem.Activities.Presentation.EditingContext%29?displayProperty=fullName>|  
|Analyseurs|CD0022|  
  
<a name="diagnostic23"></a>   
## <a name="23-new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a>23 : nouvelles surcharges Dispatcher.Invoke (ambigus) peut entraîner un comportement différent  
  
|||  
|-|-|  
|Détails|Le .NET Framework 4.5 ajoute de nouvelles surcharges pour Dispatcher.Invoke qui incluent un paramètre de type System.Action. Lorsque le code existant est recompilé, les compilateurs peuvent résoudre les appels aux méthodes Dispatcher.Invoke qui ont un paramètre de délégué en tant que les appels aux méthodes Dispatcher.Invoke avec un paramètre System.Action. Si un appel à une surcharge Dispatcher.Invoke avec un paramètre de délégué est résolu comme un appel à une surcharge Dispatcher.Invoke avec un paramètre System.Action, les différences de comportement suivantes peuvent se produire :<br /><br /> Si une exception se produit, les événements Dispatcher.UnhandledExceptionFilter et Dispatcher.UnhandledException ne sont pas déclenchés. Au lieu de cela, les exceptions sont gérées par l’événement UnobservedTaskException.<br /><br /> Les appels à certains membres, tels que DispatcherOperation.Result, bloquent jusqu'à ce que l’opération est terminée.|  
|Suggestion|Pour éviter toute ambiguïté (et les différences potentielles exception gestion ou le blocage des comportements), code Dispatcher.Invoke appelant peut passer un vide object [] en tant que deuxième paramètre à l’appel Invoke que de la résolution de la surcharge de méthode .NET 4.0.|  
|Portée|Secondaire|  
|Version|4.5|  
|Type|Reciblage|  
|API affectés|[Dispatcher.Invoke (délégué, de l’objet\<xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> [Dispatcher.Invoke (objet délégué, TimeSpan,\<xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.TimeSpan%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> [Dispatcher.Invoke (objet délégué, TimeSpan, DispatcherPriority,\<xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.TimeSpan%2CSystem.Windows.Threading.DispatcherPriority%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> [Dispatcher.Invoke (objet délégué, DispatcherPriority,\<xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.Windows.Threading.DispatcherPriority%2CSystem.Object%5B%5D%29?displayProperty=fullName>|  
|Analyseurs|CD0023|  
  
<a name="diagnostic24"></a>   
## <a name="24-encoderparameter-ctor-is-obsolete"></a>24 : EncoderParameter constructeur est obsolète  
  
|||  
|-|-|  
|Détails|Le `EncoderParameter.EncoderParameter(Encoder, Int32, Int32, Int32)` constructeur est désormais obsolète et introduire des avertissements de génération si utilisé.|  
|Suggestion|Bien que le `EncoderParameter.EncoderParameter(Encoder, Int32, Int32, Int32)` constructeur continueront de fonctionner, le constructeur suivant doit être utilisé à la place pour éviter l’avertissement de build obsolète lors de la compilation de nouveau code avec les outils de .NET 4.5 : [EncoderParameter.EncoderParameter (encodeur, Int32, EncoderParameterValueType, IntPtr)](https://msdn.microsoft.com/en-us/library/hh875096\(v=vs.110\).aspx).|  
|Portée|Secondaire|  
|Version|4.5|  
|Type|Reciblage|  
|API affectés|<xref:System.Drawing.Imaging.EncoderParameter.%23ctor%28System.Drawing.Imaging.Encoder%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>|  
|Analyseurs|CD0024|  
  
<a name="diagnostic26"></a>   
## <a name="26-change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>26 : changement de comportement pour les méthodes Task.WaitAll avec des arguments de délai d’attente  
  
|||  
|-|-|  
|Détails|Task.WaitAll comportement a été rendu plus cohérent dans .NET 4.5.<br /><br /> Dans le .NET Framework 4, ces méthodes se comportaient de manière incohérente. Lorsque le délai d’attente a expiré, si une ou plusieurs tâches étaient terminées ou annulées avant l’appel de méthode, la méthode a levé une exception AggregateException. Lorsque le délai d’attente a expiré, si aucune tâche n’était terminée ou annulée avant l’appel de méthode, mais une ou plusieurs tâches adoptaient ces États après l’appel de méthode, la méthode a retourné false.<br />Dans le .NET Framework 4.5, ces surcharges de méthode retournent désormais false si toutes les tâches sont toujours en cours d’exécution lorsque le délai d’attente a expiré, et elles lèvent une exception AggregateException uniquement si une tâche d’entrée a été annulée (qu’elle soit avant ou après l’appel de méthode) et aucune autre tâche n’est en cours d’exécution.|  
|Suggestion|Si une AggregateException a été détectée comme un moyen de détecter une tâche qui a été annulée avant l’appel de WaitAll appelé que code doit faire à la place de la détection même via la propriété IsCanceled (par exemple :. Tout (t => t.IsCanceled)) depuis .NET 4.6 uniquement dans ce cas si lève toutes les tâches ayant fait l’objet sont effectuées avant le délai d’attente.|  
|Portée|Secondaire|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|[Task.WaitAll (tâche\<xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.Int32%29?displayProperty=fullName><br /><br /> [Task.WaitAll (tâche\<xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.Int32%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> [Task.WaitAll (tâche\<xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.TimeSpan%29?displayProperty=fullName>|  
|Analyseurs|CD0026|  
  
<a name="diagnostic27"></a>   
## <a name="27-change-in-behavior-in-data-definition-language-ddl-apis"></a>27 : changement de comportement de langage DDL (Data Definition) API  
  
|||  
|-|-|  
|Détails|Le comportement des API DDL lorsque AttachDBFilename est spécifié a été modifié comme suit :<br /><br /> Chaînes de connexion pas besoin de spécifier une valeur catalogue Initial. Auparavant, AttatchDBFilename et catalogue Initial étaient nécessaire.<br /><br /> Si AttatchDBFilename et catalogue Initial sont spécifiés et que le fichier MDF donné existe, la méthode ObjectContext.DatabaseExists retourne true. Auparavant, il a retourné false.<br /><br /> Si AttatchDBFilename et catalogue Initial sont spécifiés et que le fichier MDF donné existe, l’appel de la méthode ObjectContext.DeleteDatabase supprime les fichiers.<br /><br /> Si ObjectContext.DeleteDatabase est appelé lorsque la chaîne de connexion spécifie une valeur de AttachDBFilename avec un MDF n’existe pas et un catalogue Initial n’existe pas, la méthode lève une exception InvalidOperationException. Auparavant, il a levé une exception SqlException.|  
|Suggestion|Ces modifications facilitent la création d'outils et d'applications qui utilisent les API DDL. Elles peuvent avoir une incidence sur la compatibilité des applications dans les scénarios suivants :<br /><br /> L’utilisateur écrit du code qui exécute une commande DROP DATABASE directement au lieu d’appeler ObjectContext.DeleteDatabase si ObjectContext.DatabaseExists renvoie la valeur true. Ce comportement altère le code existant si la base de données n'est pas liée mais que le fichier MDF existe.<br /><br /> L’utilisateur écrit du code qui attend que la méthode ObjectContext.DeleteDatabase pour lever une exception SqlException plutôt que d’une exception InvalidOperationException lorsque le fichier de catalogue Initial et MDF n’existent pas.|  
|Portée|Secondaire|  
|Version|4.5|  
|Type|Exécution|  
|Analyseurs|CD0027|  
  
<a name="diagnostic28"></a>   
## <a name="28-machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>28 : MachineKey.Encode et MachineKey.Decode sont désormais obsolètes  
  
|||  
|-|-|  
|Détails|Ces méthodes sont désormais obsolètes. La compilation du code qui appelle ces méthodes génère un avertissement du compilateur.|  
|Suggestion|Les alternatives recommandées sont [MachineKey.Protect](https://msdn.microsoft.com/en-us/library/system.web.security.machinekey.protect\(v=vs.110\).aspx) et [MachineKey.Unprotect](https://msdn.microsoft.com/en-us/library/system.web.security.machinekey.unprotect\(v=vs.110\).aspx). Vous pouvez également les avertissements de build peuvent être supprimés ou ils peuvent être évités à l’aide d’un compilateur antérieur. Les API sont toujours pris en charge.|  
|Portée|Secondaire|  
|Version|4.5|  
|Type|Reciblage|  
|API affectés|<xref:System.Web.Security.MachineKey.Decode%28System.String%2CSystem.Web.Security.MachineKeyProtection%29?displayProperty=fullName><br /><br /> [MachineKey.Encode (octets\<xref:System.Web.Security.MachineKey.Encode%28System.Byte%5B%5D%2CSystem.Web.Security.MachineKeyProtection%29?displayProperty=fullName>|  
|Analyseurs|CD0028|  
  
<a name="diagnostic29"></a>   
## <a name="29-the-replace-method-in-odata-urls-is-disabled-by-default"></a>29 : la méthode de remplacement dans les URL OData est désactivée par défaut  
  
|||  
|-|-|  
|Détails|À compter de .NET Framework 4.5, la méthode Replace dans les URL OData est désactivée par défaut. Lorsque vous remplacez d’OData est désactivé (désormais par défaut), toutes les demandes utilisateur, y compris les fonctions de remplacement (qui sont rares) échoue.|  
|Suggestion|Si la méthode de remplacement est nécessaire (ce qui est rare), il peut être réactivée via un [les paramètres de configuration](https://msdn.microsoft.com/en-us/library/system.data.services.configuration.dataservicesfeaturessection.replacefunction.aspx). Toutefois, une méthode de remplacement activé peut ouvrir des failles de sécurité et ne doit être utilisée qu’après un examen minutieux.|  
|Portée|Bord|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Data.Services.DataService%601?displayProperty=fullName>|  
|Analyseurs|CD0029|  
  
<a name="diagnostic30"></a>   
## <a name="30-systemservicemodelwebwebservicehost-object-no-longer-adds-a-default-endpoint"></a>30 : objet des System.ServiceModel.Web.WebServiceHost n’ajoute plus un point de terminaison par défaut  
  
|||  
|-|-|  
|Détails|L’objet des System.ServiceModel.Web.WebServiceHost n’ajoute plus un point de terminaison par défaut si un point de terminaison explicite a été ajouté par le code d’application.|  
|Suggestion|Si les utilisateurs s’attendent à pouvoir se connecter à un point de terminaison par défaut et d’autres points de terminaison explicites ont été ajoutées à la WebServiceHost, points de terminaison par défaut doivent également être ajoutés explicitement (en utilisant AddDefaultEndpoints).|  
|Portée|Secondaire|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.ServiceModel.Description.ServiceEndpoint%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%2CSystem.Uri%29?displayProperty=fullName>|  
|Analyseurs|CD0030A<br /><br /> CD0030B|  
  
<a name="diagnostic31"></a>   
## <a name="31-eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>31 : EventSource.WriteEvent impl doit passer WriteEvent les mêmes paramètres qu’il a reçue (plus ID)  
  
|||  
|-|-|  
|Détails|Le runtime applique à présent le contrat qui spécifie les éléments suivants : une classe dérivée de la source d’événement qui définit une méthode d’événement ETW doit appeler la méthode EventSource.WriteEvent avec l’ID d’événement suivi par les mêmes arguments passés à la méthode d’événement ETW.|  
|Suggestion|Une exception IndexOutOfRangeException est levée si un écouteur d’événement lit des données EventSource dans le processus pour une source d’événements qui ne respecte pas ce contrat.|  
|Portée|Secondaire|  
|Version|4.5.1|  
|Type|Exécution|  
|Analyseurs|CD0031|  
  
<a name="diagnostic32"></a>   
## <a name="32-minfreememorypercentagetoactiveservice-is-now-respected"></a>32 : MinFreeMemoryPercentageToActiveService est respectée maintenant  
  
|||  
|-|-|  
|Détails|Ce paramètre détermine la mémoire minimale qui doit être disponible sur le serveur avant l’activation d’un service WCF. Il est conçu pour éviter les exceptions OutOfMemoryException. Dans le .NET Framework 4.5, ce paramètre est sans effet. Dans le .NET Framework 4.5.1, ce paramètre est observé.|  
|Suggestion|Une exception se produit si la mémoire disponible sur le serveur web est inférieure au pourcentage défini par le paramètre de configuration. Certains services WCF qui ont réussi à démarrer et à s'exécuter dans un environnement où la mémoire est limitée risquent à présent d'échouer.|  
|Portée|Secondaire|  
|Version|4.5.1|  
|Type|Exécution|  
|Analyseurs|CD0032|  
  
<a name="diagnostic33"></a>   
## <a name="33-xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a>33 : extension d’entité XmlTextReader DTD est limitée à 10 000 000 caractères  
  
|||  
|-|-|  
|Détails|Extension d’entité DTD est désormais limité à 10 000 000 caractères. Le chargement des fichiers XML sans extension d'entité DTD ou avec une extension d'entité DTD limitée reste inchangé. Les fichiers avec des entités DTD qui s'étendent à plus de 10 000 000 caractères ne se chargent pas et lèvent désormais une exception.|  
|Suggestion|Si la limite de l’extension d’entité DTD est 10 000 000 trop faible, la valeur peut être substituée avec le [XmlReaderSettings.MaxCharactersFromEntities](https://msdn.microsoft.com/en-us/library/system.xml.xmlreadersettings.maxcharactersfromentities%28v=vs.110%29.aspx) propriété. Un XmlReaderSettings avec la valeur MaxCharactersFromEntity appropriée peut être passé à [XmlReader.Create](https://msdn.microsoft.com/en-us/library/System.Xml.XmlReader.Create\(v=vs.110\).aspx)|  
|Portée|Bord|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Xml.XmlTextReader.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%2CSystem.Xml.XmlNodeType%2CSystem.Xml.XmlParserContext%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.TextReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.TextReader%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.Stream%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.TextReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.TextReader%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.Xml.XmlNodeType%2CSystem.Xml.XmlParserContext%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader?displayProperty=fullName>|  
|Analyseurs|CD0033|  
  
<a name="diagnostic35"></a>   
## <a name="35-xslt-style-sheet-exception-message-changed"></a>35 : message d’exception de feuille de style XSLT modifié  
  
|||  
|-|-|  
|Détails|Dans le .NET Framework 4.5, le texte du message d’erreur lorsqu’un fichier XSLT est trop complexe est « la feuille de style est trop complexe. » Dans les versions antérieures, le message d'erreur était « Erreur de compilation XSLT. ». Le code d'application qui dépend du texte du message d'erreur ne fonctionne plus. Toutefois, les types d’exception restent les mêmes, cette modification n’aura aucun impact réel.|  
|Suggestion|Mettre à jour d’aucun code d’application en fonction du message excepton à partir de cette condition d’erreur à attendre le nouveau message, ou (encore mieux) mettre à jour le code pour qu’elle dépende uniquement le type d’exception ([XsltException](https://msdn.microsoft.com/en-us/library/system.xml.xsl.xsltexception\(v=vs.110\).aspx)), qui n’a pas changé.|  
|Portée|Bord|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|[XslCompiledTransform.Load (MethodInfo, Byte\[\], Type\<xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Reflection.MethodInfo%2CSystem.Byte%5B%5D%2CSystem.Type%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.String%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XPath.IXPathNavigable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XPath.IXPathNavigable%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XmlReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XmlReader%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName>|  
|Analyseurs|CD0035|  
  
<a name="diagnostic36"></a>   
## <a name="36-wf-serializes-expressionsliteralt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>36 : WF sérialise Expressions.Literal<> \</> \> dates différemment maintenant (interrompt les analyseurs XAML personnalisés)  
  
|||  
|-|-|  
|Détails|Associé au [ValueSerializer](https://msdn.microsoft.com/en-us/library/system.windows.markup.valueserializer\(v=vs.110\).aspx) objet convertit une valeur DateTime ou DateTimeOffset objet dont les composants seconde et milliseconde sont différente de zéro et (pour une valeur DateTime de valeurs) dont la propriété DateTime.Kind n’est pas non spécifiée pour la syntaxe d’élément de propriété au lieu d’une chaîne. Cette modification permet d’être un aller-retour des valeurs DateTime et DateTimeOffset. Les analyseurs XAML personnalisés qui supposent que l'entrée XAML figure dans la syntaxe d'attribut ne fonctionnent pas correctement.|  
|Suggestion|Cette modification permet d’être un aller-retour des valeurs DateTime et DateTimeOffset. Les analyseurs XAML personnalisés qui supposent que l'entrée XAML figure dans la syntaxe d'attribut ne fonctionnent pas correctement.|  
|Portée|Bord|  
|Version|4.5|  
|Type|Exécution|  
|Analyseurs|CD0036|  
  
<a name="diagnostic37"></a>   
## <a name="37-new-enum-values-in-wpfs-pagerangeselection"></a>37 : nouvelles valeurs enum dans WPF PageRangeSelection  
  
|||  
|-|-|  
|Détails|Deux nouveaux membres (CurrentPage et SelectedPage) ont été ajoutés à la [PageRangeSelection](https://msdn.microsoft.com/en-us/library/system.windows.controls.pagerangeselection\(v=vs.110\).aspx) enum.|  
|Suggestion|Dans la plupart des cas, ces modifications n’affecte pas le code utilisateur. Code qui dépend d’un certain nombre d’éléments existants dans Enum.GetNames ou Enum.GetValues appelle sur la PageRangeSelection type doit être modifié, cependant.|  
|Portée|Bord|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName>|  
|Analyseurs|CD0037|  
  
<a name="diagnostic38"></a>   
## <a name="38-wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>38 : WPF DispatcherSynchronizationContext.CreateCopy renvoie à présent une copie au lieu de l’instance actuelle  
  
|||  
|-|-|  
|Détails|Dans le .NET Framework 4, DispatcherSynchronizationContext.CreateCopy() renvoyé une référence à l’instance actuelle, principalement comme une optimisation des performances. Dans le .NET Framework 4.5, il retourne une nouvelle instance, ce qui rend possible pour la première fois de conclure que les références égales indiquent que le thread en cours d’exécution est dans le contexte de synchronisation correcte.  Il est peu probable que le code qui vérifie l’identité de ces références est affectée, mais en raison de la modification, le code qui appelle DispatcherSynchronizationContext.CreateCopy doit être testé dans le cadre de la migration vers le .NET Framework 4.5 ou version ultérieure.|  
|Suggestion|N’oubliez pas que DispatcherSynchronizationContext.CreateCopy() renvoie désormais un nouvel objet de SynchronizationContext.  Auparavant, code qui a utilisé l’équivalence des références généré de cette manière pas réellement vérifiait si elle était dans le contexte approprié, mais ne construit sur .NET 4.5 ou version ultérieure.  Bien que pas susceptible de provoquer des problèmes, exercer les chemins de code concernés doit suffire pour déterminer si cela pose un problème.|  
|Portée|Secondaire|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=fullName>|  
|Analyseurs|CD0038|  
  
<a name="diagnostic39"></a>   
## <a name="39-systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>39 : System.Threading.Tasks.Task ne lèvent plus ObjectDisposedException après suppression de l’objet  
  
|||  
|-|-|  
|Détails|À l’exception de Task.IAsyncResult.AsyncWaitHandle, System.Threading.Tasks.Task méthodes n’est plus une exception ObjectDisposedException après suppression de l’objet.<br />Cette modification prend en charge l'utilisation des tâches mises en cache. Par exemple, une méthode peut retourner une tâche mise en cache pour représenter une opération déjà terminée au lieu d'allouer une nouvelle tâche. Cette opération était impossible dans les versions précédentes du .NET Framework, car tout consommateur de la tâche pouvait la supprimer, ce qui la rendait inutilisable.|  
|Suggestion|N’oubliez pas que les méthodes de tâche peuvent lever n’est plus ObjectDisposedExceptions dans le cas lorsque l’objet est supprimé. Si une application a été en fonction de savoir qu’une tâche a été supprimée de cette exception, il doit être mis à jour pour vérifier explicitement l’état de la tâche à l’aide de [Task.Status](https://msdn.microsoft.com/en-us/library/system.threading.tasks.task.status\(v=vs.110\).aspx).|  
|Portée|Secondaire|  
|Version|4.5|  
|Type|Exécution|  
|Analyseurs|CD0039|  
  
<a name="diagnostic40"></a>   
## <a name="40-different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>40 : différentes exceptions pour les méthodes ObjectContext.CreateDatabase et DbProviderServices.CreateDatabase  
  
|||  
|-|-|  
|Détails|À compter de .NET 4.5, cas d’échec de la création de la base de données, `CreateDatabase` méthodes tente de supprimer la base de données vide. Si cette opération réussit, l’original `SQLException` seront propagées (au lieu du `InvalidOperationException` qui a été levée toujours dans .NET 4.0)|  
|Suggestion|Lorsque vous les interceptez une exception InvalidOperationException lors de l’exécution ObjectContext.CreateDatabase ou DbProviderServices.CreateDatabase, SQLExceptions doivent désormais également être interceptées.|  
|Portée|Secondaire|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Data.Common.DbProviderServices.CreateDatabase%28System.Data.Common.DbConnection%2CSystem.Nullable%7BSystem.Int32%7D%2CSystem.Data.Metadata.Edm.StoreItemCollection%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName>|  
|Analyseurs|CD0040|  
  
<a name="diagnostic41"></a>   
## <a name="41-objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>41 : ObjectContext.Translate et ObjectContext.ExecuteStoreQuery prennent désormais en charge type enum  
  
|||  
|-|-|  
|Détails|Dans .NET 4.0, le paramètre générique `T` de `ObjectContext.Translate` et `ObjectContext.ExecuteStoreQuery` méthodes n’a pas pu être une énumération. Ce scénario est maintenant pris en charge.|  
|Suggestion|Si la traduction ou ExecuteStoreQuery a été appelé sur un type enum dans .NET 4.0, « 0 » a été retourné. Si ce comportement n’est pas souhaitable, les appels doivent être remplacées par une constante 0 (ou l’équivalent de l’énumération de celui-ci).|  
|Portée|Bord|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|[ObjectContext.ExecuteStoreQuery<>\>(chaîne, objet\<xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601%28System.String%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> [ObjectContext.ExecuteStoreQuery<>\>(String, String, MergeOption, objet\<xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601%28System.String%2CSystem.String%2CSystem.Data.Objects.MergeOption%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.Translate%60%601%28System.Data.Common.DbDataReader%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.Translate%60%601%28System.Data.Common.DbDataReader%2CSystem.String%2CSystem.Data.Objects.MergeOption%29?displayProperty=fullName>|  
|Analyseurs|CD0041|  
  
<a name="diagnostic42"></a>   
## <a name="42-enumerableemptytresult-always-returns-cached-instance"></a>42 : Enumerable.Empty<> \</> \> toujours retourne mises en cache l’instance  
  
|||  
|-|-|  
|Détails|À compter de .NET 4.5, `Enumerable.Empty` retourne toujours une instance mise en cache interne `IEnumerable<T>`.<br /><br /> Auparavant, `Enumerable.Empty` serait cache vide `IEnumerable<T>` au moment de l’API a été appelée, ce qui signifie que dans certaines conditions dans lesquelles `Enumerable.Empty` a été appelé rapidement et simultanément, différentes instances du type peuvent être retournés pour différents appels à l’API.|  
|Suggestion|Étant donné que le comportement précédent est non déterministe, code est peu probable en dépendent. Toutefois, dans le cas peu probable où vides énumérables sont comparés et doit parfois être inégaux, tableaux vides explicites doivent être créés (`new T[0]`) au lieu d’utiliser `Enumerable.Empty`.|  
|Portée|Bord|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=fullName>|  
|Analyseurs|CD0042|  
  
<a name="diagnostic43"></a>   
## <a name="43-httprequestcontentencoding-property-prohibits-utf7"></a>43 : HttpRequest.ContentEncoding propriété interdit UTF7  
  
|||  
|-|-|  
|Détails|À compter de .NET Framework 4.5, l’encodage UTF-7 est interdit dans les corps des HttpRequests. Les données des applications qui dépendent des données UTF-7 entrantes ne seront pas décodées correctement dans certains cas.|  
|Suggestion|Dans l’idéal, les applications doivent être mis à jour pour ne pas utiliser l’encodage UTF-7 dans HttpRequests. Ou bien, le comportement hérité peut être restaurée à l’aide de la `aspnet:AllowUtf7RequestContentEncoding` attribut de la [appSettings](https://msdn.microsoft.com/en-us/library/hh975440\(v=vs.110\).aspx) élément.|  
|Portée|Bord|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Web.HttpRequest.ContentEncoding?displayProperty=fullName>|  
|Analyseurs|CD0043|  
  
<a name="diagnostic44"></a>   
## <a name="44-httputilityjavascriptstringencode-escapes-ampersand"></a>44 : HttpUtility.JavaScriptStringEncode d’échappement « et commercial »  
  
|||  
|-|-|  
|Détails|À compter de .NET Framework 4.5, JavaScriptStringEncode échappe le caractère esperluette (&).|  
|Suggestion|Si votre application dépend du comportement précédent de cette méthode, vous pouvez ajouter un paramètre d’aspnet:JavaScriptDoNotEncodeAmpersand les [élément appSettings ASP.NET](https://msdn.microsoft.com/en-us/library/hh975440\(v=vs.110\).aspx) dans votre fichier de configuration.|  
|Portée|Secondaire|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Web.HttpUtility.JavaScriptStringEncode%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Web.HttpUtility.JavaScriptStringEncode%28System.String%2CSystem.Boolean%29?displayProperty=fullName>|  
|Analyseurs|CD0044A<br /><br /> CD0044B|  
  
<a name="diagnostic46"></a>   
## <a name="46-eventlistener-truncates-strings-with-embedded-nulls"></a>46 : EventListener tronque les chaînes comportant des valeurs null incorporées  
  
|||  
|-|-|  
|Détails|EventListener tronque les chaînes avec des valeurs null incorporées. Caractères null ne sont pas pris en charge par la classe EventSource. La modification affecte uniquement les applications qui utilisent EventListener pour lire les données EventSource dans le processus et qui utilisent des caractères null comme délimiteurs.|  
|Suggestion|EventSource données doivent être mises à jour, si possible, pour ne pas utiliser les caractères null incorporés.|  
|Portée|Bord|  
|Version|4.5.1|  
|Type|Exécution|  
|API affectés|<xref:System.Diagnostics.Tracing.EventListener.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%2CSystem.Diagnostics.Tracing.EventKeywords%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%2CSystem.Diagnostics.Tracing.EventKeywords%2CSystem.Collections.Generic.IDictionary%7BSystem.String%2CSystem.String%7D%29?displayProperty=fullName> \</String, String>|  
|Analyseurs|CD0046|  
  
<a name="diagnostic48"></a>   
## <a name="48-obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>48 : ObsoleteAttribute exporte ObsoleteAttribute et DeprecatedAttribute dans les scénarios de WinMD  
  
|||  
|-|-|  
|Détails|Lorsque vous créez une bibliothèque de métadonnées Windows (fichier .winmd), l’attribut ObsoleteAttribute est exportée en tant que ObsoleteAttribute et Windows.Foundation.DeprecatedAttribute.|  
|Suggestion|La recompilation du code source existant qui utilise l’attribut ObsoleteAttribute peut générer des avertissements lors de l’utilisation de ce code à partir de C++ / CX ou JavaScript.<br /><br /> Nous ne recommandons pas l’application ObsoleteAttribute et Windows.Foundation.DeprecatedAttribute au code dans des assemblys managés ; Cela peut entraîner des avertissements de génération.|  
|Portée|Bord|  
|Version|4.5.1|  
|Type|Reciblage|  
|Analyseurs|CD0048A<br /><br /> CD0048B|  
  
<a name="diagnostic49"></a>   
## <a name="49-resolveassemblyreference-task-now-warns-on-dependencies-with-the-wrong-architecture"></a>49 : ResolveAssemblyReference, tâche avertit désormais des dépendances avec une architecture incorrecte  
  
|||  
|-|-|  
|Détails|La tâche émet un avertissement, MSB3270, qui indique qu’une référence ou l’une de ses dépendances ne correspond pas à l’architecture de l’application. Par exemple, cela se produit si une application qui a été compilée avec l’option anycpu inclut un x86 référence. Ainsi, l'application peut échouer au moment de l'exécution (si l'application est déployée en tant que processus x64 dans notre exemple).|  
|Suggestion|Deux domaines sont impactés :<br /><br /> La recompilation génère des avertissements qui n'étaient pas apparus quand l'application avait été compilée sous une version antérieure de MSBuild. En revanche, étant donné que l'avertissement identifie une source potentielle d'échec du runtime, vous devez l'examiner et le traiter.<br /><br /> Si les avertissements sont considérés comme des erreurs, la compilation de l'application échouera.|  
|Portée|Secondaire|  
|Version|4.5.1|  
|Type|Reciblage|  
|Analyseurs|CD0049|  
  
<a name="diagnostic51"></a>   
## <a name="51-wpf-textbox-defaults-to-undo-limit-of-100"></a>51 : zone de texte WPF par défaut pour annuler la limite de 100  
  
|||  
|-|-|  
|Détails|Dans le .NET 4.5, la limite d’annulation par défaut pour une zone de texte WPF est de 100 (par opposition à un nombre illimité de .NET 4.0)|  
|Suggestion|Si une limite d’annulation de 100 est trop faible, la limite de peut être définie explicitement avec la propriété UndoLimit de la zone de texte|  
|Portée|Bord|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Windows.Controls.TextBox?displayProperty=fullName>|  
|Analyseurs|CD0051|  
  
<a name="diagnostic55"></a>   
## <a name="55-exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a>55 : exceptions pendant le traitement non prise en charge dans System.Threading.Tasks.Task se propagent n’est plus sur le thread finaliseur  
  
|||  
|-|-|  
|Détails|Étant donné que la classe System.Threading.Tasks.Task représente une opération asynchrone, elle intercepte toutes les exceptions sans gravité qui se produisent pendant le traitement asynchrone. Dans le .NET Framework 4.5, si une exception n’est pas respectée et que votre code n’attend jamais la tâche, l’exception ne sera plus se propager sur le thread finaliseur et arrêtera le processus pendant le garbage collection. Cette modification améliore la fiabilité des applications qui utilisent la classe de tâche pour effectuer le traitement asynchrone non pris en charge.|  
|Suggestion|Si une application dépend des exceptions asynchrones non prise en charge propager vers le thread finaliseur, le comportement précédent peut être restauré en fournissant un gestionnaire approprié pour le [TaskScheduler.UnobservedTaskException](https://msdn.microsoft.com/en-us/library/system.threading.tasks.taskscheduler.unobservedtaskexception\(v=vs.110\).aspx) événement, ou en définissant un [élément de configuration d’exécution](https://msdn.microsoft.com/en-us/library/jj160346%28v=vs.110%29.aspx).|  
|Portée|Bord|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Action%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%60%600%7D%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%60%600%7D%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7B%60%600%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7B%60%600%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Start?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Start%28System.Threading.Tasks.TaskScheduler%29?displayProperty=fullName>|  
|Analyseurs|CD0055|  
  
<a name="diagnostic58"></a>   
## <a name="58-iasyncresultcompletedsynchronously-property-must-be-correct-for-the-resulting-task-to-complete"></a>58 : IAsyncResult.CompletedSynchronously propriété doit être correcte pour la tâche obtenue se termine  
  
|||  
|-|-|  
|Détails|Lors de l’appel TaskFactory.FromAsync, l’implémentation de la propriété IAsyncResult.CompletedSynchronously doit être correcte pour la tâche obtenue se termine. Autrement dit, la propriété doit retourner la valeur true si et seulement si, l’implémentation effectuée de façon synchrone. Auparavant, la propriété n'était pas vérifiée.|  
|Suggestion|Si les implémentations de IAsyncResult correctement retournent trues pour la propriété CompletedSynchronusly uniquement lorsqu’une tâche effectuée de façon synchrone, aucun interruption ne seront appliqués. Les utilisateurs doivent vérifier qu’ils possèdent (le cas échéant) pour vous assurer qu’ils évaluent correctement si une tâche terminée de manière synchrone ou non des implémentations de IAsyncResult.|  
|Portée|Bord|  
|Version|4.5|  
|Type|Reciblage|  
|API affectés|<xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Object%29?displayProperty=fullName> \</AsyncCallback, Object, IAsyncResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</AsyncCallback, Object, IAsyncResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Threading.Tasks.TaskCreationOptions%2CSystem.Threading.Tasks.TaskScheduler%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Object%29?displayProperty=fullName> \</IAsyncResult, TResult> \</AsyncCallback, Object, IAsyncResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</IAsyncResult, TResult> \</AsyncCallback, Object, IAsyncResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2CSystem.Object%29?displayProperty=fullName> </TArg1, AsyncCallback, Object, IAsyncResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</TArg1, AsyncCallback, Object, IAsyncResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%29?displayProperty=fullName> \</IAsyncResult, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</IAsyncResult, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Threading.Tasks.TaskCreationOptions%2CSystem.Threading.Tasks.TaskScheduler%29?displayProperty=fullName> \</IAsyncResult, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%601%7D%2C%60%600%2CSystem.Object%29?displayProperty=fullName> \</IAsyncResult, TResult> \</TArg1, AsyncCallback, Object, IAsyncResult> \</TArg1, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%601%7D%2C%60%600%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</IAsyncResult, TResult> \</TArg1, AsyncCallback, Object, IAsyncResult> \</TArg1, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2CSystem.Object%29?displayProperty=fullName> </TArg1, TArg2, AsyncCallback, Object, IAsyncResult> </TArg1, TArg2><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</TArg1, TArg2, AsyncCallback, Object, IAsyncResult> \</TArg1, TArg2><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%602%7D%2C%60%600%2C%60%601%2CSystem.Object%29?displayProperty=fullName> \</IAsyncResult, TResult> \</TArg1, TArg2, AsyncCallback, Object, IAsyncResult> \</TArg1, TArg2, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%602%7D%2C%60%600%2C%60%601%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</IAsyncResult, TResult> \</TArg1, TArg2, AsyncCallback, Object, IAsyncResult> \</TArg1, TArg2, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%29?displayProperty=fullName> </TArg1, TArg2, TArg3, AsyncCallback, Object, IAsyncResult> </TArg1, TArg2, TArg3><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</TArg1, TArg2, TArg3, AsyncCallback, Object, IAsyncResult> \</TArg1, TArg2, TArg3><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%603%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%29?displayProperty=fullName> \</IAsyncResult, TResult> \</TArg1, TArg2, TArg3, AsyncCallback, Object, IAsyncResult> \</TArg1, TArg2, TArg3, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%603%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</IAsyncResult, TResult> \</TArg1, TArg2, TArg3, AsyncCallback, Object, IAsyncResult> \</TArg1, TArg2, TArg3, TResult>|  
|Analyseurs|CD0058|  
  
<a name="diagnostic59"></a>   
## <a name="59-log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>59 : nom du fichier journal créé par la méthode ObjectContext.CreateDatabase a changé pour correspondre aux spécifications de SQL Server  
  
|||  
|-|-|  
|Détails|Lorsque la méthode CreateDatabase est appelée directement ou à l’aide de Code First avec le fournisseur SqlClient et une valeur de AttachDBFilename dans la chaîne de connexion, il crée un fichier journal nommé filename_log.ldf au lieu de filename.ldf (où filename est le nom du fichier spécifié par la valeur AttachDBFilename). Cette modification améliore le débogage en fournissant un fichier journal dont le nom répond aux spécifications SQL Server.|  
|Suggestion|Si le nom du fichier journal est important pour une application, l’application doit être mis à jour pour attendre le format de nom de fichier standard _log.ldf.|  
|Portée|Bord|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName>|  
|Analyseurs|CD0059|  
  
<a name="diagnostic60"></a>   
## <a name="60-pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>60 : Page.LoadComplete événement n’entraîne plus contrôle System.Web.UI.WebControls.EntityDataSource à appeler une liaison de données  
  
|||  
|-|-|  
|Détails|Le `Page.LoadComplete` événement ne force plus le contrôle System.Web.UI.WebControls.EntityDataSource à appeler une liaison de données pour les modifications apportées aux paramètres de création/mise à jour/suppression. Cette modification supprime un aller-retour superflu vers la base de données, empêche les valeurs des contrôles de réinitialisation et produit un comportement qui est cohérent avec d’autres contrôles de données, tels que SqlDataSource et ObjectDataSource. Elle produit un comportement différent dans le cas peu probable où les applications dépendraient de l'appel de la liaison de données dans l'événement `Page.LoadComplete`.|  
|Suggestion|S’il est nécessaire pour la liaison de données, appeler manuellement la méthode databind dans un événement qui est plus haut dans le renvoi.|  
|Portée|Bord|  
|Version|4.5|  
|Type|Exécution|  
|Analyseurs|CD0060|  
  
<a name="diagnostic61"></a>   
## <a name="61-webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a>61 : WebUtility.HtmlDecode décode ne sont plus des séquences d’entrée non valides  
  
|||  
|-|-|  
|Détails|Par défaut, les méthodes de décodage ne décodent plus une séquence d'entrée non valide en une chaîne UTF-16 non valide. Au lieu de cela, elles retournent l'entrée d'origine.|  
|Suggestion|Le changement lié à la sortie du décodeur doit importer uniquement si vous stockez des données binaires à la place de données UTF-16 dans les chaînes. Pour contrôler explicitement ce comportement, affectez la `aspnet:AllowRelaxedUnicodeDecoding` attribut de la [appSettings](https://msdn.microsoft.com/en-us/library/ms228154\(v=vs.110\).aspx) élément à True pour activer les comportement hérité ou false pour activer le comportement actuel.|  
|Portée|Secondaire|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Net.WebUtility.HtmlDecode%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Net.WebUtility.HtmlDecode%28System.String%2CSystem.IO.TextWriter%29?displayProperty=fullName><br /><br /> <xref:System.Net.WebUtility.UrlDecode%28System.String%29?displayProperty=fullName>|  
|Analyseurs|CD0061|  
  
<a name="diagnostic63"></a>   
## <a name="63-apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>63 : les applications publiées avec ClickOnce qui utilisent un certificat de signature de code SHA-256 peuvent échouer sur Windows 2003  
  
|||  
|-|-|  
|Détails|L'exécutable est signé avec SHA256. Auparavant, il était signé avec SHA1, que le certificat de signature du code ait été SHA-1 ou SHA-256. Cela s'applique à :<br /><br /> toutes les applications générées avec Visual Studio 2012 ou une version ultérieure ;<br /><br /> toutes les applications générées avec Visual Studio 2010 (ou version antérieure) en présence de .NET Framework 4.5.<br /><br /> En outre, si .NET Framework 4.5 (ou une version ultérieure) est présent, le manifeste ClickOnce est également signé avec SHA-256 pour les certificats SHA-256, quelle que soit la version du .NET Framework sur laquelle il a été compilé.|  
|Suggestion|Le changement de signature exécutable ClickOnce affecte uniquement les systèmes Windows Server 2003 ; ils requièrent que KB 938397 soit installé.<br /><br /> Le changement de signature du manifeste avec l'algorithme SHA-256 même quand une application cible .NET Framework 4.0, ou des versions antérieures, présente une dépendance de runtime sur .NET Framework 4.5 ou version ultérieure.|  
|Portée|Bord|  
|Version|4.5-4.6|  
|Type|Reciblage|  
|Analyseurs|CD0063|  
  
<a name="diagnostic68"></a>   
## <a name="68-dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a>68 : DbParameter.Precision et DbParameter.Scale sont désormais membres virtuels public  
  
|||  
|-|-|  
|Détails|DbParameter.Precision et DbParameter.Scale sont implémentées en tant que propriétés virtuelles publiques. Elles remplacent les implémentations d’interface explicites correspondantes, DbParameter.IDbDataParameter.Precision et DbParameter.IDbDataParameter.Scale.|  
|Suggestion|Lors de la nouvelle génération d’un fournisseur de base de données ADO.NET, ces différences nécessite le mot clé « override » à appliquer aux propriétés de précision et d’échelle. Cela est nécessaire uniquement lors de la création de nouveau les composants. les fichiers binaires existants continueront de fonctionner.|  
|Portée|Secondaire|  
|Version|4.5.1|  
|Type|Reciblage|  
|API affectés|<xref:System.Data.Common.DbParameter.Precision?displayProperty=fullName><br /><br /> <xref:System.Data.Common.DbParameter.Scale?displayProperty=fullName>|  
|Analyseurs|CD0068|  
  
<a name="diagnostic73"></a>   
## <a name="73-dataobjectgetdata-now-retrieves-data-as-utf-8"></a>73 : DataObject.GetData récupère maintenant les données au format UTF-8  
  
|||  
|-|-|  
|Détails|Pour les applications qui ciblent le .NET Framework 4 ou qui s’exécutent sur .NET Framework 4.5.1 ou des versions antérieures, DataObject.GetData récupère les données au format HTML sous forme de chaîne ASCII. Ainsi, les caractères non-ASCII (caractères dont les codes ASCII sont supérieurs à 0x7F) sont représentés par deux caractères aléatoires.<br /><br /> Pour les applications qui ciblent le .NET Framework 4.5 ou version ultérieur et s’exécutent sur le .NET Framework 4.5.2, `DataObject.GetData` récupère les données au format HTML au format UTF-8, qui représentent correctement les caractères supérieurs à 0x7F.|  
|Suggestion|Si vous avez implémenté une solution de contournement pour le problème de codage des chaînes au format HTML (par exemple, en codant explicitement la chaîne HTML récupérée à partir du Presse-papiers en la passant à la méthode UTF8Encoding.GetString) et que vous reciblez votre application à partir de la version 4 vers la version 4.5, cette solution doit être supprimée.<br /><br /> Si l’ancien comportement est nécessaire pour une raison quelconque, l’application peut cibler .NET Framework 4.0 pour obtenir ce comportement.|  
|Portée|Bord|  
|Version|4.5.2|  
|Type|Reciblage|  
|API affectés|<xref:System.Windows.DataObject.GetData%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Windows.DataObject.GetData%28System.String%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Windows.DataObject.GetData%28System.Type%29?displayProperty=fullName>|  
|Analyseurs|CD0073|  
  
<a name="diagnostic75"></a>   
## <a name="75-targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>75 : TargetFrameworkName pour le domaine d’application par défaut ne sont plus par défaut, null si non défini  
  
|||  
|-|-|  
|Détails|Le TargetFrameworkName a été précédemment null dans le domaine d’application par défaut, sauf si elle a été définie explicitement. À compter de 4.6, la propriété TargetFrameworkName pour le domaine d’application par défaut a la valeur par défaut dérivée TargetFrameworkAttribute (s’il en existe). Domaines d’application par défaut non continue à hériter leur TargetFrameworkName le domaine d’application par défaut (qui ne sera pas par défaut null dans 4.6) sauf si elle est substituée explicitement.|  
|Suggestion|Code doit être mis à jour pour qu’elle ne dépende pas `AppDomainSetup.TargetFrameworkName` par défaut null. S’il est nécessaire que cette propriété continue prendre la valeur null, elle peut être explicitement définie à cette valeur.|  
|Portée|Bord|  
|Version|4.6|  
|Type|Exécution|  
|API affectés|<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName>|  
|Analyseurs|CD0075B<br /><br /> CD0075A|  
  
<a name="diagnostic76"></a>   
## <a name="76-x509certificate2tostringbool-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>76 : X509Certificate2.ToString(bool) ne lève pas maintenant lorsque .NET ne peut pas gérer le certificat  
  
|||  
|-|-|  
|Détails|Auparavant, cette méthode serait lever si 'true' a été transmise pour le paramètre verbose et comportait des certificats installés n’étaient pas pris en charge par le .net Framework. À présent, la méthode réussit et retourne une chaîne valide qui omet les parties inaccessibles de le certifiate.|  
|Suggestion|N’importe quel code en fonction de X509Certificate2.ToString(bool) doit être mis à jour pour attendre que la chaîne retournée peut exclure certaines données de certificat (telles que la clé publique, clé privée et les extensions) dans certains cas dans lequel l’API aurait précédemment levée.|  
|Portée|Bord|  
|Version|4.6|  
|Type|Exécution|  
|API affectés|<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString%28System.Boolean%29?displayProperty=fullName>|  
|Analyseurs|CD0076|  
  
<a name="diagnostic77"></a>   
## <a name="77-reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>77 : les objets de réflexion peuvent ne plus être passés du code managé aux clients DCOM d’out-of-process  
  
|||  
|-|-|  
|Détails|Les objets de réflexion ne peuvent plus être passés du code managé aux clients DCOM hors processus. Les types suivants sont concernés :<br /><br /> Assembly<br /><br /> MemberInfo (et ses types dérivés, y compris FieldInfo, MethodInfo, Type et TypeInfo)<br /><br /> MethodBody<br /><br /> Module<br /><br /> ParameterInfo.<br /><br /> Les appels à `IMarshal` pour l’objet de retour `E_NOINTERFACE`.|  
|Suggestion|Mettre à jour le code de marshaling pour travailler avec des objets non-réflexion|  
|Portée|Secondaire|  
|Version|4.6|  
|Type|Exécution|  
|Analyseurs|CD0077|  
  
<a name="diagnostic78"></a>   
## <a name="78-contentdisposition-datetimes-returns-slightly-different-string"></a>78 : ContentDisposition DateTimes renvoie une chaîne légèrement différente  
  
|||  
|-|-|  
|Détails|Représentations sous forme de chaîne de ContentDispositions ont été modifiées, à compter de 4.6, toujours représentent le composant d’heure d’une valeur DateTime avec deux chiffres. Il s’agit de se conformer aux [RFC822](http://www.ietf.org/rfc/rfc0822.txt) et [RFC2822](http://www.ietf.org/rfc/rfc2822.txt). Cela entraîne `ContentDisposition.ToString` pour retourner une chaîne légèrement différente dans 4.6 dans les scénarios où un des éléments de la disposition est antérieure à 10:00. Notez que ContentDispositions sont sérialisées parfois les convertir en chaînes, afin de n’importe quel ContentDisposition ToString opérations, la sérialisation ou GetHashCode appels doivent être examinées.|  
|Suggestion|N’attendent pas que représentations sous forme de chaîne de ContentDispositions à partir de différentes versions du .NET Framework comparera correctement à l’autre. Convertir les chaînes vers ContentDispositions, si possible, avant d’effectuer une comparaison.|  
|Portée|Secondaire|  
|Version|4.6|  
|Type|Exécution|  
|API affectés|<xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=fullName><br /><br /> <xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=fullName>|  
|Analyseurs|CD0078|  
  
<a name="diagnostic82"></a>   
## <a name="82-workflowdesignerload-doesnt-remove-symbol-property"></a>82 : WorkflowDesigner.Load ne supprime pas les propriétés de symbole  
  
|||  
|-|-|  
|Détails|Lorsque vous ciblez le .NET Framework 4.5 dans le Concepteur de flux de travail et le chargement d’un flux de travail 3.5 hébergé à nouveau avec la méthode WorkflowDesigner.Load(), une XamlDuplicateMemberException est levée lors de l’enregistrement du flux de travail.|  
|Suggestion|Ce bogue se manifeste uniquement lors du ciblage de .NET Framework 4.5 dans le Concepteur de flux de travail, afin qu’il peut être contourné en définissant le `WorkflowDesigner.Context.Services.GetService<DesignerConfigurationService>().TargetFrameworkName` pour le .NET Framework 4.0.<br /><br /> Vous pouvez également, le problème peut être évité en utilisant la [WorkflowContext.Load(string)](https://msdn.microsoft.com/en-us/library/ee425926\(v=vs.110\).aspx) méthode pour charger le flux de travail, au lieu de [WorkflowDesigner.Load()](https://msdn.microsoft.com/en-us/library/ee403482\(v=vs.110\).aspx).|  
|Portée|Majeur|  
|Version|4.5-4.5.2|  
|Type|Reciblage|  
|API affectés|<xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=fullName>|  
|Analyseurs|CD0082|  
  
<a name="diagnostic83"></a>   
## <a name="83-sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>83 : SqlConnection.Open échoue sur Windows 7 avec non IFS Winsock BSP ou LSP présent  
  
|||  
|-|-|  
|Détails|SqlConneciton.Open et OpenAsync échouent dans le .NET Framework 4.5 s’exécute sur un ordinateur Windows 7 avec un non IFS Winsock BSP ou un LSP est présent sur l’ordinateur.<br /><br /> Pour déterminer si un non - IFS BSP ou un LSP est installé, utilisez le `netsh WinSock Show Catalog` de commandes et examiner chaque `Winsock Catalog Provider Entry` élément retourné. Si la valeur des indicateurs de Service a le `0x20000` bit défini, le fournisseur utilise des gestionnaires de IFS et fonctionnera correctement. Si la `0x20000` est effacé (non défini), elle est non - IFS BSP ou LSP.|  
|Suggestion|Ce bogue a été résolu dans le .NET Framework 4.5.2, afin qu’il peut être évité par la mise à niveau de .NET Framework. Sinon, il peut être évité en supprimant toute installé non - IFS LSP Winsock.|  
|Portée|Secondaire|  
|Version|4.5-4.5.2|  
|Type|Exécution|  
|API affectés|<xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=fullName><br /><br /> <xref:System.Data.SqlClient.SqlConnection.OpenAsync%28System.Threading.CancellationToken%29?displayProperty=fullName>|  
|Analyseurs|CD0083|  
  
<a name="diagnostic84"></a>   
## <a name="84-icommandcanexecutechanged-event-behaviour-changed-in-net-45"></a>84 : comportement d’événement ICommand.CanExecuteChanged a changé dans .NET 4.5  
  
|||  
|-|-|  
|Détails|Dans le .NET Framework 4.5, un CanExecuteChangedEvent a été ignoré, sauf si l’expéditeur de l’événement est le même objet que l’objet qui a déclenché l’événement. Ce bogue a été corrigé dans les mises à jour de .NET Framework 4.5 servcing.|  
|Suggestion|Ce bogue a été résolu dans le .NET Framework 4.5 versions, de maintenance de sorte qu’il peut être évité en effectuant la mise à jour de .NET Framework ou par mise à niveau vers .NET Framework 4.5.1. Sinon, code d’application à l’aide de ICommand modifiables pour vous assurer que l’expéditeur lors du déclenchement d’une commande CanExecuteChanged est identique à l’objet déclenchant l’événement.|  
|Portée|Secondaire|  
|Version|4.5-4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=fullName>|  
|Analyseurs|CD0084|  
  
<a name="diagnostic85"></a>   
## <a name="85-some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>85 : certaines API .NET provoquer de première chance (géré) EntryPointNotFoundExceptions  
  
|||  
|-|-|  
|Détails|Dans le .NET Framework 4.5, un petit nombre de méthodes .NET a commencé à lever EntryPointNotFoundExceptions de première chance. Ces exceptions ont été traitées dans le .net Framework, mais peut interrompre l’automatisation des tests qui ne vous attendiez pas les exceptions de première chance. Ces mêmes API interrompre certains scénarios d’ApiVerifier lorsque HighVersionLie est activé.|  
|Suggestion|Ce problème peut être évité par la mise à niveau vers .NET Framework 4.5.1. Également, d’automatisation des tests peut être mise à jour pour ne pas s’arrêter sur EntryPointNotFoundExceptions de première chance.|  
|Portée|Bord|  
|Version|4.5-4.5.1|  
|Type|Exécution|  
|API affectés|<xref:System.Diagnostics.Debug.Assert%28System.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%2CSystem.String%29?displayProperty=fullName><br /><br /> [Debug.Assert (booléen, chaîne, chaîne, objet\<xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%29?displayProperty=fullName>|  
|Analyseurs|CD0085|  
  
<a name="diagnostic86"></a>   
## <a name="86-scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>86 : un TreeView WPF ou une ListBox groupée dans un VirtualizingStackPanel de défilement peut provoquer un blocage  
  
|||  
|-|-|  
|Détails|Dans le .NET Framework&4;.5, le défilement d’un contrôle TreeView WPF dans un panneau d’empilement virtualisé peut provoquer se bloque s’il existe des marges dans la fenêtre d’affichage (entre les éléments dans l’arborescence, par exemple, ou sur un élément ItemsPresenter). En outre, dans certains cas, différents éléments de tailles de la vue peuvent provoquer l’instabilité du même s’il n’existe aucun marges.|  
|Suggestion|Ce problème peut être évité par la mise à niveau vers .NET Framework 4.5.1. Vous pouvez également les marges peuvent être supprimées à partir des collections d’affichage (tels que des arborescences) dans les volets de pile virtualisé si tous les éléments ont la même taille.|  
|Portée|Majeur|  
|Version|4.5-4.5.1|  
|Type|Exécution|  
|API affectés|<xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing%28System.Windows.DependencyObject%2CSystem.Boolean%29?displayProperty=fullName>|  
|Analyseurs|CD0086<br /><br /> CD0086|  
  
<a name="diagnostic89"></a>   
## <a name="89-typeisassignablefrom-returns-wrong-result-for-generic-variables-with-constraints"></a>89 : Type.IsAssignableFrom retourne un résultat incorrect pour les variables génériques avec des contraintes  
  
|||  
|-|-|  
|Détails|Dans le .NET Framework 4.5, Type.IsAssignableFrom renvoie incorrectement `false` dans tous les cas pour certains types génériques avec des contraintes.|  
|Suggestion|Ce problème a été corrigé dans une mise à jour de maintenance. Mettez à jour .NET Framework 4.5, ou mise à niveau vers .NET Framework 4.5.1 ou version ultérieur, pour résoudre ce problème. Vous pouvez également éviter d’utiliser des IsAssignableFrom avec des types génériques qui ont des contraintes sur les paramètres génériques. API de réflexion peut être utilisé comme une solution de contournement.|  
|Portée|Secondaire|  
|Version|4.5-4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Type.IsAssignableFrom%28System.Type%29?displayProperty=fullName>|  
|Analyseurs|CD0089<br /><br /> CD0089|  
  
<a name="diagnostic91"></a>   
## <a name="91-entityframework-60-loads-very-slowly-in-apps-launched-from-visual-studio"></a>91 : Entity Framework 6.0 charge très lentement dans les applications lancées à partir de Visual Studio  
  
|||  
|-|-|  
|Détails|Lancement d’une application à partir de Visual Studio 2013 qui utilise Entity Framework 6.0 peut être très lente.|  
|Suggestion|Ce problème est résolu dans EntityFramework 6.0.2. Mettez à jour EntityFramework pour éviter le problème de performance.|  
|Portée|Bord|  
|Version|4.5|  
|Type|Exécution|  
|Analyseurs|CD0091|  
  
<a name="diagnostic92"></a>   
## <a name="92-multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>92 : zone de texte multiligne ASP.Net espacement modifié lors de l’utilisation de AntiXSSEncoder  
  
|||  
|-|-|  
|Détails|Dans .NET Framework 4.0, des lignes supplémentaires ont été insérés entre les lignes d’une zone de texte multiligne lors de la publication, si vous utilisez le `AntiXSSEncoder`. Dans le .NET Framework 4.5, les sauts de ligne superflus sont pas inclus, mais uniquement si l’application web cible .NET 4.5|  
|Suggestion|N’oubliez pas que les applications web 4.0 reciblées vers .NET 4.5 peuvent avoir des zones de texte multiligne améliorées pour insérer des sauts de ligne supplémentaire n’est plus. Si ce n’est pas souhaitable, l’application peut avoir l’ancien comportement lors de l’exécution sur le .NET Framework 4.5 en ciblant le .NET Framework 4.0.|  
|Portée|Secondaire|  
|Version|4.5|  
|Type|Reciblage|  
|Analyseurs|CD0092|  
  
<a name="diagnostic95"></a>   
## <a name="95-concurrentqueuettrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>95 : ConcurrentQueue<>\>. TryPeek peut retourner une valeur null erronée via son paramètre de sortie  
  
|||  
|-|-|  
|Détails|Dans certains scénarios multithreads, `ConcurentQueue<T>.TryPeek` peut retourner la valeur true, mais renseigner le paramètre de sortie avec une valeur null (au lieu de la valeur correcte, lu).|  
|Suggestion|Ce problème est résolu dans le .NET Framework 4.5.1. Mise à niveau vers cette infrastructure pour résoudre le problème.|  
|Portée|Majeur|  
|Version|4.5-4.5.1|  
|Type|Exécution|  
|API affectés|<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek%28%600%40%29?displayProperty=fullName>|  
|Analyseurs|CD0095|  
  
<a name="diagnostic98"></a>   
## <a name="98-multiple-items-in-a-single-tablelayoutpanel-cell-may-be-rearranged"></a>98 : plusieurs éléments dans une cellule TableLayoutPanel peuvent être réorganisées.  
  
|||  
|-|-|  
|Détails|Dans le .NET Framework 4.5, si plusieurs éléments sont placés dans la même cellule du TableLayoutPanel, ils peuvent s’afficher dans un ordre différent de ceux de .NET Framework 4.0.|  
|Suggestion|Ce comportement a été rétabli dans une mise à jour de maintenance pour le .NET Framework 4.5. Mettez à jour .NET Framework 4.5, ou mise à niveau vers .NET Framework 4.5.1 ou version ultérieur, pour résoudre ce problème. Vous pouvez également éviter le cas de plusieurs éléments dans la même cellule TableLayourPanel ambiguë.|  
|Portée|Secondaire|  
|Version|4.5-4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Windows.Forms.TableLayoutControlCollection.Add%28System.Windows.Forms.Control%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>|  
|Analyseurs|CD0098|  
  
<a name="diagnostic100"></a>   
## <a name="100-foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>100 : variable d’itérateur Foreach est désormais étendue au sein de l’itération, donc la sémantique de capture de fermeture est différente (dans C#&5;)  
  
|||  
|-|-|  
|Détails|Variables d’itération foreach à partir de c# 5 (Visual Studio 2012), sont limitées au sein de l’itération. Cela peut provoquer des sauts si le code a été précédemment selon les variables à ne pas inclus dans la fermeture de foreach. Le symptôme de ce changement est qu’une variable d’itérateur transmise à un delagate est considérée comme la valeur qu’elle avait au moment que le délégué a été créé, au lieu de la valeur qu’elle avait au moment que le délégué a été appelé.|  
|Suggestion|Dans l’idéal, code doit être mis à jour pour prévoir le nouveau comportement du compilateur. Si la sémantique anciennes est requise, la variable d’itérateur peut être remplacée par une variable distincte qui est placée explicitement en dehors de la portée de la boucle.|  
|Portée|Majeur|  
|Version|4.5|  
|Type|Reciblage|  
|Analyseurs|CD0100|  
  
<a name="diagnostic101"></a>   
## <a name="101-htmltextwriter-does-not-render-br-element-correctly"></a>101 : HtmlTextWriter n’effectue pas le rendu\`<br>\>' élément correctement  
  
|||  
|-|-|  
|Détails|À compter de .NET Framework 4.6, appelant `HtmlTextWriter.RenderBeginTag()` et `HtmlTextWriter.RenderEndTag()` avec un `<BR />` élément insère correctement seul `<BR />` (au lieu de deux)|  
|Suggestion|Si une application dépendait supplémentaire `<BR />` balise, `HtmlTextWriter.RenderBeginTag()` doit être appelée une deuxième fois. Notez que ce comportement affecte uniquement les applications qui ciblent le .NET Framework 4.6, une autre option consiste à cibler une version antérieure du .NET Framework afin d’obtenir l’ancien comportement.|  
|Portée|Bord|  
|Version|4.6|  
|Type|Reciblage|  
|API affectés|<xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName>|  
|Analyseurs|CD0101|  
  
<a name="diagnostic104"></a>   
## <a name="104-calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>104 : Items.Refresh appel sur un contrôle ListBox WPF, ListView ou DataGrid avec des éléments sélectionnés peut provoquer des doublons apparaissent dans l’élément  
  
|||  
|-|-|  
|Détails|Dans le .NET Framework 4.5, l’appel ListBox.Items.Refresh à partir de code tandis que les éléments sont sélectionnés dans une zone de liste peut provoquer les éléments sélectionnés à être dupliqué dans la liste. Un problème similaire se produit avec ListView et DataGrid. Ce problème est résolu dans le .NET Framework 4.6.|  
|Suggestion|Ce problème peut être contourné en désélectionnant par programme des éléments avant que l’actualisation est appelée et en sélectionnant nouveau les après que l’appel est terminé. Sinon, ce problème a été résolu dans le .NET Framework 4.6 et peut être adressé par la mise à niveau vers cette version du .NET Framework.|  
|Portée|Secondaire|  
|Version|4.5-4.6|  
|Type|Exécution|  
|API affectés|<xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName>|  
|Analyseurs|CD0104|  
  
<a name="diagnostic105"></a>   
## <a name="105-etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>105 : ETW EventListeners ne capture pas les événements provenant des fournisseurs avec les mots clés explicites (par exemple, le fournisseur de la bibliothèque parallèle de tâches)  
  
|||  
|-|-|  
|Détails|EventListeners ETW avec un masque de mot clé vide ne capturez pas correctement les événements provenant des fournisseurs avec les mots clés explicites. Dans le .NET Framework 4.5, le fournisseur de la bibliothèque parallèle de tâches a commencé en fournissant des mots clés explicites et a déclenché ce problème. Dans le .NET Framework 4.6, EventListeners ont été mis à jour pour ne plus avoir ce problème.|  
|Suggestion|Pour contourner ce problème, remplacez les appels à EnableEvents (eventSource, niveau) avec les appels à la surcharge EnableEvents qui spécifie explicitement le masque « tous les mots clés » à utiliser : `EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))`.<br /><br /> Sinon, ce problème a été résolu dans le .NET Framework 4.6 et peut être adressé par la mise à niveau vers cette version du .NET Framework.|  
|Portée|Bord|  
|Version|4.5-4.6|  
|Type|Exécution|  
|API affectés|<xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%29?displayProperty=fullName>|  
|Analyseurs|CD0105|  
  
<a name="diagnostic109"></a>   
## <a name="109-building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>109 : création d’un edmx Entity Framework avec Visual Studio 2013 peut échouer avec l’erreur MSB4062 si vous utilisez les tâches EntityDeploySplit ou EntityClean  
  
|||  
|-|-|  
|Détails|Outils MSBuild 12.0 (inclus dans Visual Studio 2013) modifié les emplacements de fichier msbuild, à l’origine des anciens fichiers de cibles d’Entity Framework n’était pas valide. Le résultat est que `EntityDeploySplit` et `EntityClean` tâches échouent, car ils ne parviennent pas à trouver `Microsoft.Data.Entity.Build.Tasks.dll`. Notez que ce saut est pas en raison d’une modification de l’ensemble d’outils (msbuild/VS), en raison d’une modification de .NET Framework. Il se produit uniquement lors de la mise à niveau des outils de développement, ne pas simplement la mise à niveau du .NET Framework.|  
|Suggestion|Fichiers de cibles Entity Framework sont fixes pour travailler avec le début de disposition msbuild nouvelle dans le .NET Framework 4.6. Mise à niveau vers cette version du Framework permet de résoudre ce problème. Vous pouvez également [cela](http://stackoverflow.com/a/24249247/131944) solution de contournement peut être utilisée pour corriger les fichiers cibles directement.|  
|Portée|Majeur|  
|Version|4.5.1-4.6|  
|Type|Reciblage|  
|Analyseurs|CD0109|  
  
<a name="diagnostic111"></a>   
## <a name="111-xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>111 : validation de schéma XSD maintenant détecte correctement les violations de contraintes unique si les clés composées sont utilisés et d’une clé est vide  
  
|||  
|-|-|  
|Détails|Versions du .NET Framework antérieures à 4.6 présentaient un bogue qui a provoqué la validation XSD de ne pas détecter les contraintes uniques pour les clés composées si une des clés est vide. Dans le .NET Framework 4.6, ce problème est résolu. Cela entraîne une validation plus correcte, mais elle peut également provoquer du code XML non validation qui auraient précédemment.|  
|Suggestion|Si elle est plus souple, validation de .NET Framework 4.0 est nécessaire, l’application de validation peut cibler la version 4.5 (ou version antérieure) du .NET Framework. Lorsque le reciblage à .NET 4.6, toutefois, révision du code doit être effectuée pour vous assurer que les clés composées en double (comme décrit dans la description de ce numéro) ne devraient pas valider.|  
|Portée|Bord|  
|Version|4.6|  
|Type|Reciblage|  
|Analyseurs|CD0111|  
  
<a name="diagnostic112"></a>   
## <a name="112-calling-attributegetcustomattributes-on-an-indexer-property-no-longer-throws-ambiguousmatchexception-if-the-ambiguity-can-be-resolved-by-indexs-type"></a>112 : Attribute.GetCustomAttributes appel sur une propriété d’indexeur ne lève plus AmbiguousMatchException si l’ambiguïté peut être résolue par type d’index  
  
|||  
|-|-|  
|Détails|Avant le .NET Framework 4.6, l’appel `GetCustomAttribute(s)` sur un indexeur propriété différait à partir d’une autre propriété uniquement par le type de l’index entraînerait une `AmbiguousMatchException`. À compter de .NET Framework 4.6, les attributs de la propriété seront correctement retournées.|  
|Suggestion|N’oubliez pas que GetCustomAttribute(s) ne fonctionnera plus fréquemment maintenant. Si une application a été précédemment compter sur le `AmbiguousMatchException`, réflexion doit maintenant être utilisée pour rechercher explicitement plusieurs indexeurs, à la place.|  
|Portée|Bord|  
|Version|4.6|  
|Type|Exécution|  
|API affectés|<xref:System.Attribute.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName>|  
|Analyseurs|CD0112|  
  
<a name="diagnostic113"></a>   
## <a name="113-intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>113 : par intermittence Impossible de faire défiler à l’élément bas ItemsControls (telles que la zone de liste et DataGrid) lors de l’utilisation de DataTemplates personnalisé  
  
|||  
|-|-|  
|Détails|Dans certains cas, un bogue dans le .NET Framework 4.5 est à l’origine ItemsControls (comme le contrôle ListBox, ComboBox, DataGrid, etc.) parchemin pas à leur élément bas lors de l’utilisation de DataTemplates personnalisé. Si le défilement est tenté une deuxième fois (après le défilement sauvegarder), il fonctionnera ensuite.|  
|Suggestion|Ce problème a été résolu dans le .NET Framework 4.5.2 et peut être adressé par la mise à niveau vers cette version (ou une version ultérieure) du .NET Framework. Également, les utilisateurs peuvent continuer à faire glisser les barres de défilement aux articles finals de ces collections, mais pouvez être amené à deux reprises faire correctement.|  
|Portée|Secondaire|  
|Version|4.5-4.5.2|  
|Type|Exécution|  
|Analyseurs|CD0113|  
  
<a name="diagnostic114"></a>   
## <a name="114-glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-45"></a>114 : GlyphRun.ComputeInkBoundingBox() et FormattedText.Extent retournent des valeurs différentes à compter de .NET 4.5  
  
|||  
|-|-|  
|Détails|Des améliorations ont été apportées à GlyphRun.ComputeInkBoundingBox() et FormattedText.Extent dans le .NET Framework 4.5 pour résoudre les problèmes où les zones ont été trop petites pour les glyphes contenus dans certains cas, dans le .NET Framework 4.0. Par conséquent, certaines zones englobantes sera supérieure à compter de .NET Framework 4.5, ce qui entraîne des différences subtiles dans la disposition de l’interface utilisateur.|  
|Suggestion|N’oubliez pas que des tailles de zone englobante glyphe ont augmenté. Ces évolutions vont améliorer généralement de présentation et de tests d’atteinte, mais si vous souhaitez le comportement (versions antérieures au .NET 4.5) plus ancien, il peut être choisie en ajoutant l’entrée suivante au fichier app.config :<br /><br /> `<appsettings> <add key="IncludeAllInkInBoundingBox" value="false"> </appsettings>`|  
|Portée|Bord|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=fullName><br /><br /> <xref:System.Windows.Media.FormattedText.Extent?displayProperty=fullName>|  
|Analyseurs|CD0114|  
  
<a name="diagnostic124"></a>   
## <a name="124-calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>124 : DataGrid.CommitEdit appel à partir d’un gestionnaire CellEditEnding supprime le focus  
  
|||  
|-|-|  
|Détails|Appeler DataGrid.CommitEdit à partir d’un des gestionnaires d’événements du DataGrid CellEditEnding provoque la DataGrid perd le focus.|  
|Suggestion|Ce bogue a été résolu dans le .NET Framework 4.5.2, afin qu’il peut être évité par la mise à niveau de .NET Framework. Sinon, il peut être évité explicitement en sélectionnant à nouveau le contrôle DataGrid après l’appel de CommitEdit.|  
|Portée|Bord|  
|Version|4.5-4.5.2|  
|Type|Exécution|  
|API affectés|<xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName><br /><br /> <xref:System.Windows.Controls.DataGrid.CommitEdit%28System.Windows.Controls.DataGridEditingUnit%2CSystem.Boolean%29?displayProperty=fullName>|  
|Analyseurs|CD0124|  
  
<a name="diagnostic125"></a>   
## <a name="125-aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>125 : ASP.NET MVC échappe maintenant les espaces dans les chaînes transmises via des paramètres d’itinéraire  
  
|||  
|-|-|  
|Détails|Afin de se conformer à la norme RFC 2396, espaces dans les chemins de routage sont maintenant pris en compte lors du remplissage des paramètres d’action à partir d’un itinéraire. Par conséquent, tandis que `/controller/action/some data` précédemment correspondent à l’itinéraire `/controller/action/{data}` et fournir `some data` comme paramètre de données, il fournit désormais `some%20data` à la place.|  
|Suggestion|Code doit être mis à jour pour éliminer les paramètres de chaîne à partir d’un itinéraire. Si l’URI d’origine est nécessaire, vous pouvez y accéder avec l’API Request.RequestUri.OriginalString.|  
|Portée|Secondaire|  
|Version|4.5.2|  
|Type|Exécution|  
|API affectés|<xref:System.Web.Http.RouteAttribute.%23ctor%28System.String%29?displayProperty=fullName>|  
|Analyseurs|CD0125|  
  
<a name="diagnostic127"></a>   
## <a name="127-vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>127 : VB.NET ne prend plus en qualification d’espace de noms partielle pour System.Windows APIs  
  
|||  
|-|-|  
|Détails|À compter de .NET 4.5.2, projets VB.NET ne peut pas spécifier System.Windows APIs avec des espaces de noms partiellement qualifiés. Par exemple, la référence à `Windows.Forms.DialogResult` échoue. Au lieu de cela, code doit faire référence au nom qualifié complet (`System.Windows.Forms.DialogResult`) ou importer l’espace de noms et faire référence simplement à `DialogResult`.|  
|Suggestion|Code doit être mis à jour pour faire référence à `System.Windows` API avec des noms simples (et l’importation de l’espace de noms pertinents) ou avec des noms qualifiés complets.|  
|Portée|Secondaire|  
|Version|4.5.2|  
|Type|Reciblage|  
|Analyseurs|CD0127|  
  
<a name="diagnostic129"></a>   
## <a name="129-two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>129 : liaison de données bidirectionnelle à une propriété avec un accesseur Set non public n’est pas pris en charge.  
  
|||  
|-|-|  
|Détails|Tentative de liaison de données à une propriété sans accesseur Set public n’a jamais été un scénario pris en charge. À compter de .NET Framework 4.5.1, ce scénario lève une exception InvalidOperationException. Notez que cette nouvelle exception sera levée uniquement pour les applications ciblant spécifiquement .NET Framework 4.5.1. Si une application cible le .NET Framework 4.5, l’appel est autorisé. Si l’application ne cible pas une version particulière du .NET Framework, la liaison sera traitée en tant qu’unidirectionnelles.|  
|Suggestion|L’application doit être mis à jour pour utiliser une liaison unidirectionnelle ou exposer publiquement des accesseur Set de la propriété. Vous pouvez également ciblant le .NET Framework 4.5 entraîne l’application à l’ancien comportement.|  
|Portée|Secondaire|  
|Version|4.5.1|  
|Type|Reciblage|  
|API affectés|<xref:System.Windows.Data.BindingMode?displayProperty=fullName>|  
|Analyseurs|CD0129|  
  
<a name="diagnostic130"></a>   
## <a name="130-marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>130 : Marshal.SizeOf et Marshal.PtrToStructure surcharges saut dynamique code  
  
|||  
|-|-|  
|Détails|À compter de .NET Framework 4.5.1, liaison dynamique pour les méthodes `Marshal.SizeOf` ou `Marshal.PtrToStructure` (via Windows PowerShell, IronPython ou le mot-clé c# dynamique, par exemple) peut entraîner `MethodInvocationExceptions` nouvelles surcharges de ces méthodes ont été ajoutés qui peuvent être ambiguës pour les moteurs de script.|  
|Suggestion|Mettre à jour des scripts pour indiquer clairement qui doit être de surcharge utilisée. Cela peut généralement effectué par un cast explicite des paramètres de type des méthodes comme `System.Type`. Consultez la page [ce lien](https://support.microsoft.com/en-us/kb/2909958/) pour plus de détails et d’exemples illustrant comment résoudre ce problème.|  
|Portée|Secondaire|  
|Version|4.5.1|  
|Type|Exécution|  
|Analyseurs|CD0130|  
  
<a name="diagnostic131"></a>   
## <a name="131-previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>131 : PreviewLostKeyboardFocus est appelée plusieurs fois si son gestionnaire affiche une boîte de message Windows Forms  
  
|||  
|-|-|  
|Détails|À compter de .NET Framework 4.5, l’appel `System.Windows.Forms.MessageBox.Show` d’un `UIElement.PreviewLostKeyboardFocus` Gestionnaire entraîne le gestionnaire à nouveau déclencher la fermeture de la boîte de message, ce qui peut entraîner une boucle infinie de boîtes de message.|  
|Suggestion|Il existe deux options pour résoudre ce problème :<br /><br /> Il peut être évité en appelant `System.Windows.MessageBox.Show` au lieu de `System.Windows.Forms.MessageBox.Show`.<br /><br /> Il peut être évité en affichant la boîte de message d’un `LostKeyboardFocus` Gestionnaire d’événements (par opposition à une `PreviewLostKeyboardFocus` Gestionnaire d’événements).|  
|Portée|Bord|  
|Version|4.5|  
|Type|Exécution|  
|API affectés|<xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=fullName>|  
|Analyseurs|CD0131|  
  
<a name="diagnostic133"></a>   
## <a name="133-a-concurrentdictionary-serialized-in-net-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-451-or-452"></a>133 : un ConcurrentDictionary sérialisé dans .NET 4.5 NetDataContractSerializer ne peut pas être désérialisé par .NET 4.5.1 ou 4.5.2  
  
|||  
|-|-|  
|Détails|En raison des modifications internes du type, `System.Collections.Concurrent.ConcurrentDictionary` les objets qui sont sérialisés avec le .NET Framework 4.5 à l’aide de la `NetDataContractSerializer` ne peut pas être désérialisé dans le .NET Framework 4.5.1 ou dans le .NET Framework 4.5.2.<br /><br /> Notez que l’autre direction déplacement (sérialisation avec le .NET Framework 4.5.x et désérialisation avec le .NET Framework 4.5) fonctionne. De même, ensemble de la sérialisation entre les versions 4.x fonctionne avec le .NET Framework 4.6.<br /><br /> Sérialisation et désérialisation avec une seule version du .NET Framework ne sont pas affectée.|  
|Suggestion|S’il est nécessaire de sérialiser et désérialiser un ConcurrentDictionary entre le .NET Framework 4.5 et .NET Framework 4.5.1/4.5.2, un autre sérialiseur comme le sérialiseur DataContractSerializer ou BinaryFormatter doit être utilisé à NetDataContractSerializer.<br /><br /> Vous pouvez également, car ce problème est résolu dans le .NET Framework 4.6, il peut être résolu par la mise à niveau vers cette version du .NET Framework.|  
|Portée|Secondaire|  
|Version|4.5.1-4.6|  
|Type|Exécution|  
|Analyseurs|CD0133|  
  
<a name="diagnostic134"></a>   
## <a name="134-persian-calendar-now-uses-the-hijri-solar-algorithm"></a>134 : calendrier persan utilise désormais l’algorithme SOLAIRE hégirien  
  
|||  
|-|-|  
|Détails|À compter de .NET Framework 4.6, la classe de calendrier persan utilise l’algorithme SOLAIRE hégirien. Conversion entre autres calendriers du calendrier persan peut produire un résultat légèrement différent à compter de .NET Framework 4.6 pour les dates antérieures à 1800 ou postérieures à 2023 (grégorien).<br /><br /> En outre, `PersianCalendar.MinSupportedDateTime` est désormais `March 22, 0622 instead of March 21, 0622`.|  
|Suggestion|N’oubliez pas que certaines dates de début ou à liaison tardives peuvent être légèrement différents lors de l’utilisation du calendrier persan dans .NET 4.6. En outre, lorsque vous sérialisez les dates entre les processus qui peuvent s’exécuter sur différentes versions du .NET Framework, ne stockez pas les sous forme de chaînes de date de calendrier persan (dans la mesure où ces valeurs peuvent être différentes).|  
|Portée|Secondaire|  
|Version|4.6|  
|Type|Exécution|  
|API affectés|<xref:System.Globalization.PersianCalendar?displayProperty=fullName>|  
|Analyseurs|CD0134|  
  
<a name="diagnostic138"></a>   
## <a name="138-calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>138 : CreateDefaultAuthorizationContext appelé avec un argument null a été modifié.  
  
|||  
|-|-|  
|Détails|L’implémentation de AuthorizationContext retourné par un appel à la `CreateDefaultAuthorizationContext(IList<IAuthorizationPolicy>)` avec un authorizationPolicies null argument a changé son implémentation dans le .NET Framework 4.6.|  
|Suggestion|Dans de rares cas, les applications WCF qui utilisent l'authentification personnalisée peuvent voir les différences de comportement. Dans ce cas, le comportement précédent peut être restauré de deux manières :<br /><br /> Recompiler l'application pour cibler une version antérieure du .NET Framework autre que 4.6. Pour les services hébergés dans IIS, utilisez la <httpRuntime targetframework="x.x"></httpRuntime> \> élément à cibler une version antérieure du .NET Framework.<br /><br /> Ajoutez la ligne suivante à la `<appSettings>` section de votre fichier app.config :`<add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />`|  
|Portée|Secondaire|  
|Version|4.6|  
|Type|Reciblage|  
|API affectés|<xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29?displayProperty=fullName>|  
|Analyseurs|CD0138|  
  
<a name="diagnostic141"></a>   
## <a name="141-wpf-treeviewitem-must-be-used-within-a-treeview"></a>141 : WPF TreeViewItem doit être utilisée dans un contrôle TreeView  
  
|||  
|-|-|  
|Détails|Une modification a été introduite dans 4.5 qui restreint l’utilisation d’éléments TreeViewItem en dehors d’un contrôle TreeView. Cela se manifeste dans les conditions suivantes :<br /><br /> Parent visual de TreeViewItem n’est pas un panneau de configuration. (Un TreeViewItem généré pour un contrôle TreeView aura un panneau comme son parent)<br /><br /> Le TreeViewItem est un descendant d’un VirtualizingStackPanel agissant en tant que l’hôte « éléments » pour un contrôle de liste (ListBox, DataGrid, ListView, etc.). La virtualisation ne doit être activé.<br /><br /> Le VirtualizingStackPanel est un élément de défilement (`ScrollUnit="Item"`).<br /><br /> Quelqu'un appelle `VirtualizingStackPanel.MakeVisible(v)` pour faire défiler un élément `v` dans l’affichage. Cela est possible explicitement ou implicitement dans un nombre de façons. peut-être la plus courante façon consiste simplement à cliquer sur `v` afin de lui donner le focus clavier.<br /><br /> La chaîne parent visual de `v` à la VirtualizingStackPanel traverse le TreeViewItem.<br /><br /> En d’autres termes, cela se produit lorsqu’un TreeViewItem est utilisé en dehors d’un contrôle TreeView, et l’utilisateur clique sur un descendant de la TreeViewItem à afficher. Si le TreeViewItem n’a aucun descendant pouvant être actif, vous ne verrez jamais ce problème. Un exemple d’une situation où il est atteint est lorsqu’un TreeViewItem est la racine d’un DataTemplate.  Lorsque ce problème est atteint, il existe une InvalidCastException se produit dans le cadre WPF.|  
|Suggestion|Un correctif sera disponible pour cela.|  
|Portée|Secondaire|  
|Version|4.5|  
|Type|Exécution|  
|Analyseurs|CD0141|  
  
<a name="diagnostic143"></a>   
## <a name="143-x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>143 : X509CertificateClaimSet.FindClaims considère que tous les claimTypes  
  
|||  
|-|-|  
|Détails|Dans les applications qui ciblent le .NET Framework 4.6.1, si un ensemble de revendications est initialisé à partir d’un certificat qui a plusieurs entrées DNS dans le champ de SAN, de X509 la méthode FindClaims essaie de correspondre à l’argument claimType avec toutes les entrées DNS.<br /><br /> Pour les applications qui ciblent des versions antérieures du .NET Framework, la méthode FindClaims tente de faire correspondre l’argument claimType uniquement avec la dernière entrée DNS.|  
|Suggestion|Cette modification affecte uniquement les applications qui ciblent le .NET Framework 4.6.1. Cette modification peut être désactivée (ou activé si ciblé pre-4.6.1) avec le [DisableMultipleDNSEntries](https://msdn.microsoft.com/en-us/library/mt620030%28v=vs.110%29.aspx) commutateur de compatibilité.|  
|Portée|Secondaire|  
|Version|4.6.1|  
|Type|Reciblage|  
|API affectés|<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%28System.String%2CSystem.String%29?displayProperty=fullName>|  
|Analyseurs|CD0143|  
  
<a name="diagnostic144"></a>   
## <a name="144-applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>144 : Application.FilterMessage ne lève plus d’implémentations réentrantes du IMessageFilter.PreFilterMessage  
  
|||  
|-|-|  
|Détails|Avant le .NET Framework 4.6.1, appelant Application.FilterMessage avec un IMessageFilter.PreFilterMessage les AddMessageFilter appelée RemoveMessageFilter (lors de l’appel également Application.DoEvents) provoque une exception IndexOutOfRangeException.<br /><br /> À partir d’applications qui ciblent le .NET Framework 4.6.1, cette exception ne soit plus levée et réentrantes décrite ci-dessus peut utiliser des filtres.|  
|Suggestion|N’oubliez pas que Application.FilterMessage lèvera n’est plus le comportement IMessageFilter.PreFilterMessage réentrante décrites ci-dessus. Cela affecte uniquement les applications qui ciblent le .NET Framework 4.6.1.<br /><br /> Les applications ciblant le .NET Framework 4.6.1 peuvent refuser cette modification (ou les applications ciblant des anciennes infrastructures peuvent participer) à l’aide de la [DontSupportReentrantFilterMessage](https://msdn.microsoft.com/en-us/library/mt620032%28v=vs.110%29.aspx) commutateur de compatibilité.|  
|Portée|Bord|  
|Version|4.6.1|  
|Type|Reciblage|  
|API affectés|<xref:System.Windows.Forms.Application.FilterMessage%28System.Windows.Forms.Message%40%29?displayProperty=fullName>|  
|Analyseurs|CD0144|  
  
<a name="diagnostic145"></a>   
## <a name="145-currentculture-is-not-preserved-across-wpf-dispatcher-operations"></a>145 : CurrentCulture n’est pas conservé entre les opérations de répartiteur de WPF  
  
|||  
|-|-|  
|Détails|À compter de .NET Framework 4.6, CurrentCulture ou CurrentUICulture modifiée dans un [répartiteur](https://msdn.microsoft.com/en-us/library/system.windows.threading.dispatcher%28v=vs.110%29.aspx) seront perdues à la fin de cette opération de répartiteur. De même, modifications CurrentCulture ou CurrentUICulture effectués en dehors d’une opération de répartiteur peut ne pas être répercutées lorsque que l’opération s’exécute.<br /><br /> Concrètement, cela signifie que les modifications CurrentCulture et CurrentUICulture ne peuvent pas circuler entre les rappels de WPF UI et tout autre code dans une application WPF.<br /><br /> Cela est dû à une modification de [ExecutionContext](https://msdn.microsoft.com/en-us/library/system.threading.executioncontext%28v=vs.110%29.aspx) qui provoque CurrentCulture et CurrentUICulture doit être stockée au début du contexte d’exécution avec les applications ciblant le .NET Framework 4.6. Les opérations de répartiteur WPF stockent le contexte d’exécution utilisé pour commencer l’opération et de restaurer le contexte précédent lorsque l’opération est terminée. Comme CurrentCulture et CurrentUICulture font désormais partie de ce contexte, les modifications dans une opération de répartiteur ne sont pas conservées en dehors de l’opération.|  
|Suggestion|Les applications affectées par ce changement peuvent contourner en stockant la valeur CurrentCulture souhaitée ou CurrentUICulture dans un champ et l’intégration de toutes les opérations de répartiteur organismes (y compris les gestionnaires de rappel d’événement de l’interface utilisateur) que le CurrentCulture et CurrentUICulture corrects sont définis. Vous pouvez également ExecutionContext modifier sous-jacent cette modification WPF affecte uniquement les applications ciblant le .NET Framework 4.6 ou une version ultérieure, cet arrêt peut être évité en ciblant le .NET Framework 4.5.2.|  
|Portée|Secondaire|  
|Version|4.6|  
|Type|Reciblage|  
|Analyseurs|CD0145|