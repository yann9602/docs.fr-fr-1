---
title: "Diagnostics de compatibilité .NET | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e481270-b62a-4cb4-8dda-5b4c5b59d61d
caps.latest.revision: 7
author: twsouthwick
ms.author: tasou
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 19006cc5f24ffc66b92e53e8174c6bd33c249679
ms.openlocfilehash: 06ebf87e02c8fd745d9c2f3a55eca329323a7d91
ms.lasthandoff: 04/18/2017

---
# <a name="net-compatibility-diagnostics"></a>Diagnostics de compatibilité .NET
Les diagnostics de compatibilité .NET sont des analyseurs issus de la technologie Roslyn qui permettent d’identifier les problèmes de compatibilité entre les différentes versions du .NET Framework. Cette liste contient tous les analyseurs disponibles, même si chaque migration ne nécessite qu’une partie de ces analyseurs. Les analyseurs permettent de déterminer les problèmes liés à la migration planifiée et signalent uniquement ce type de problèmes. Pour obtenir la liste des problèmes par version affectée, consultez [Compatibilité des applications](../../../docs/framework/migration-guide/application-compatibility.md).  
  
 Chaque problème comprend les informations suivantes :  
  
-   La description de ce qui a changé par rapport à la version précédente.  
  
-   La suggestion explique la façon dont ce changement affecte les clients et indique les éventuelles solutions de contournement disponibles pour préserver la compatibilité entre les versions.  
  
-   Une évaluation de l’importance du changement. Les problèmes de compatibilité entre applications sont classés de la façon suivante :  
  
    |||  
    |-|-|  
    |Majeur|Modification importante qui affecte un grand nombre d’applications ou qui nécessite de modifier significativement le code.|  
    |Mineur|Modification qui affecte un petit nombre d’applications ou qui nécessite peu de modifications du code.|  
    |Cas limite|Modification qui affecte des applications dans des scénarios très spécifiques et peu courants.|  
    |Transparent|Modification qui n’a pas d’effet visible pour le développeur ou l’utilisateur de l’application.|  
  
-   La version indique à quel moment cette modification est apparue pour la première fois dans le .NET Framework. Certaines modifications sont annulées, ce qui est également indiqué.  
  
-   Type de modification :  
  
    |||  
    |-|-|  
    |Reciblage|La modification affecte les applications qui sont recompilées pour cibler une nouvelle version du .NET Framework.|  
    |Exécution|La modification affecte une application existante qui cible une version antérieure du .NET Framework, mais s’exécute sur une version ultérieure.|  
  
-   Les API affectées, le cas échéant.  
  
-   Les ID des diagnostics disponibles  
  
<a name="diagnostic1"></a>   
## <a name="1-soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>1 : SoapFormatter ne peut pas désérialiser la table de hachage et les objets de collection ordonnée similaires  
  
|||  
|-|-|  
|Détails|SoapFormatter ne garantit pas que les objets sérialisés dans une version du .NET Framework pourront être désérialisés correctement dans une autre version. En effet, certaines collections ordonnées (comme la table de hachage) ont gagné de nouveaux membres entre les versions 4.0 et 4.5. De fait, les objets de ces types ne peuvent pas être désérialisés avec le .NET 4.0 s’ils l’ont été avec le .NET 4.5. Notez que si les données sérialisées sont sérialisées et désérialisées avec la même version du .NET Framework, aucun problème ne se produit.|  
|Suggestion|La sérialisation SoapFormatter doit être remplacée par la sérialisation BinaryFormatter ou NetDataContractSerialization pour ne pas être affecté par les modifications du .NET Framework.|  
|Portée|Mineur|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize%28System.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize%28System.IO.Stream%2CSystem.Runtime.Remoting.Messaging.HeaderHandler%29?displayProperty=fullName><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize%28System.IO.Stream%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize%28System.IO.Stream%2CSystem.Object%2CSystem.Runtime.Remoting.Messaging.Header%5B%5D%29?displayProperty=fullName>|  
|Analyseurs|CD0001B<br /><br /> CD0001A|  
  
<a name="diagnostic3"></a>   
## <a name="3-wpf-datatemplate-elements-are-now-visible-to-uia"></a>3 : Les éléments DataTemplate WPF sont désormais détectés par UI Automation  
  
|||  
|-|-|  
|Détails|Avant, les éléments DataTemplate ne pouvaient pas être détectés par UI Automation. À compter de la version 4.5, UI Automation détecte ces éléments. C’est utile dans de nombreux cas, mais cela peut empêcher l’exécution des tests qui dépendent des arborescences UIA ne contenant pas d’éléments DataTemplate.|  
|Suggestion|Les tests UI Automation pour cette application peuvent nécessiter des modifications visant à prendre en compte l’arborescence UIA qui contient désormais des éléments DataTemplate autrefois indétectables. Par exemple, les tests qui attendent des éléments contigus doivent maintenant s’attendre à ce que des éléments UIA, autrefois indétectables, se trouvent entre ces éléments. Autre exemple : Les tests qui reposent sur certains nombres ou index pour les éléments UIA peuvent nécessiter la modification de leurs valeurs.|  
|Portée|Limité|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Windows.DataTemplate.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Windows.DataTemplate.%23ctor%28System.Object%29?displayProperty=fullName>|  
|Analyseurs|CD0003|  
  
<a name="diagnostic4"></a>   
## <a name="4-wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>4 : Le texte sélectionné dans la zone de texte WPF sélectionnée s’affiche dans une autre couleur quand la zone de texte est inactive  
  
|||  
|-|-|  
|Détails|Dans le .NET 4.5, lorsqu’un contrôle de zone de texte WPF est inactif (c’est-à-dire qu’il n’a pas le focus), le texte sélectionné dans la zone s’affiche dans une couleur différente de celle utilisée lorsque le contrôle est actif.|  
|Suggestion|Le comportement précédent (celui du .NET 4.0) peut être restauré en définissant la propriété [FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported](https://msdn.microsoft.com/library/system.windows.frameworkcompatibilitypreferences.areinactiveselectionhighlightbrushkeyssupported\(v=vs.110\).aspx) avec la valeur false.|  
|Portée|Limité|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Windows.Controls.TextBox?displayProperty=fullName>|  
|Analyseurs|CD0004|  
  
<a name="diagnostic5"></a>   
## <a name="5-listtforeach-can-throw-exception-when-modifying-list-item"></a>5 : List\<T>.ForEach peut lever une exception lorsque vous modifiez un élément de la liste  
  
|||  
|-|-|  
|Détails|À compter du .NET 4.5, un énumérateur `List<T>.ForEach` lève une exception InvalidOperationException si un élément de la collection appelante est modifié. Avant, il ne levait pas d’exception, mais pouvait entraîner des conditions de concurrence.|  
|Suggestion|Dans l’idéal, le code doit être corrigé de manière à ne pas modifier les listes pendant l’énumération de leurs éléments, car cela n’est jamais une opération sûre. Cependant, pour restaurer le comportement précédent, une application peut cibler le .NET 4.0.|  
|Portée|Limité|  
|Version|4.5|  
|Type|Reciblage|  
|API affectées|<xref:System.Collections.Generic.List%601.ForEach%28System.Action%7B%600%7D%29?displayProperty=fullName>|  
|Analyseurs|CD0005|  
  
<a name="diagnostic6"></a>   
## <a name="6-systemuri-parsing-adheres-to-rfc-3987"></a>6 : L’analyse System.Uri respecte la norme RFC 3987  
  
|||  
|-|-|  
|Détails|L’analyse URI a changé à différents niveaux dans le .NET 4.5. Notez, cependant, que ces changements affectent uniquement le code qui cible le .NET 4.5. Si un fichier binaire cible le .NET 4.0, l’ancien comportement est appliqué. Les changements appliqués à l’analyse URI dans le .NET 4.5 sont les suivants :<br /><br /> L’analyse URI effectue la normalisation et la vérification des caractères selon les dernières règles IRI de la norme RFC 3987.<br /><br /> Le formulaire C de normalisation Unicode n’est appliqué que sur la partie hôte de l’URI<br /><br /> Mailto non valide : les URI provoquent désormais une exception<br /><br /> Les espaces à la fin d’un segment de tracé sont désormais conservés<br /><br /> Les URI `file://` n’échappent pas le caractère `?`<br /><br /> Les caractères de contrôle Unicode allant de `U+0080` à `U+009F` ne sont pas pris en charge<br /><br /> Les virgules `,` ou `%2c` ne sont pas automatiquement sans séquence d’échappement|  
|Suggestion|Si l’ancienne sémantique d’analyse URI du .NET 4.0 est nécessaire (et c’est souvent le cas), elle peut être utilisée en ciblant le .NET 4.0. Pour cela, utilisez un TargetFrameworkAttribute sur l’assembly ou modifiez les propriétés du projet dans l’interface utilisateur du système de projet de Visual Studio.|  
|Portée|Majeur|  
|Version|4.5|  
|Type|Reciblage|  
|API affectées|<xref:System.Uri.%23ctor%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.Uri%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.String%2CSystem.UriKind%2CSystem.Uri%40%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.Uri%2CSystem.String%2CSystem.Uri%40%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.Uri%2CSystem.Uri%2CSystem.Uri%40%29?displayProperty=fullName>|  
|Analyseurs|CD0006D<br /><br /> CD0006C<br /><br /> CD0006F<br /><br /> CD0006E<br /><br /> CD0006A<br /><br /> CD0006G<br /><br /> CD0006B|  
  
<a name="diagnostic10"></a>   
## <a name="10-systemuri-escaping-now-supports-rfc-3986-httptoolsietforghtmlrfc3986"></a>10 : L’échappement System.Uri prend désormais en charge la norme RFC 3986 (http://tools.ietf.org/html/rfc3986)  
  
|||  
|-|-|  
|Détails|L’échappement d’URI a été modifié dans le .NET 4.5 de manière à prendre en charge la norme [RFC 3986](http://tools.ietf.org/html/rfc3986). Ces modifications sont les suivantes :<br /><br /> `EscapeDataString` représente une séquence d'échappement pour les caractères réservés basés sur la norme RFC 3986.<br /><br /> `EscapeUriString` ne représente pas une séquence d'échappement pour les caractères réservés.<br /><br /> `UnescapeDataString` ne lève pas d'exception s'il rencontre une séquence d'échappement non valide.<br /><br /> Les caractères d'échappement non réservés sont sans séquence d'échappement.|  
|Suggestion|Mettez à jour les applications pour qu’elles ne comptent pas sur UnescapeDataString pour lever une exception en cas de séquence d’échappement non valide. Ces séquences sont à présent directement détectées.<br /><br /> Il est également possible que les URI avec et sans séquence d’échappement, ainsi que les chaînes de données, varient entre les versions 4.0 et 4.5 du .NET. En outre, ils ne doivent pas être comparés directement entre différentes versions du .NET. Ils doivent être analysés et normalisés dans une seule version du .NET avant de faire l’objet d’une comparaison.|  
|Portée|Mineur|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Uri.EscapeDataString%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.EscapeUriString%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.UnescapeDataString%28System.String%29?displayProperty=fullName>|  
|Analyseurs|CD0010A<br /><br /> CD0010B<br /><br /> CD0010C|  
  
<a name="diagnostic11"></a>   
## <a name="11-systemnetpeertopeercollaboration-unavailable-on-windows-8"></a>11 : System.Net.PeerToPeer.Collaboration n’est pas disponible sur Windows 8  
  
|||  
|-|-|  
|Détails|L’espace de noms System.Net.PeerToPeer.Collaboration est indisponible sur Windows 8 et versions ultérieures.|  
|Suggestion|Les applications qui prennent en charge Windows 8 et ultérieur doivent être modifiées de manière à ne pas dépendre de cet espace de noms ou de ses membres.|  
|Portée|Majeur|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Net.PeerToPeer.Collaboration?displayProperty=fullName>|  
|Analyseurs|CD0011|  
  
<a name="diagnostic12"></a>   
## <a name="12-mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>12 : Les catalogues MEF implémentent IEnumerable et ne peuvent donc plus être utilisés pour créer un sérialiseur  
  
|||  
|-|-|  
|Détails|À compter de la version 4.5 du .NET Framework, les catalogues MEF implémentent IEnumerable et ne peuvent donc plus être utilisés pour créer un sérialiseur (objet XmlSerializer). La tentative de sérialisation d'un catalogue MEF lève une exception.|  
|Suggestion|Ne peut plus utiliser un catalogue MEF pour créer un sérialiseur|  
|Portée|Majeur|  
|Version|4.5|  
|Type|Exécution|  
|Analyseurs|CD0012|  
  
<a name="diagnostic13"></a>   
## <a name="13-missing-target-framework-moniker-results-in-40-behavior"></a>13 : Un moniker manquant dans la version cible de .NET Framework a pour effet de restaurer le comportement de la version 4.0  
  
|||  
|-|-|  
|Détails|Les applications dans lesquelles un [TargetFrameworkAttribute](https://msdn.microsoft.com/library/system.runtime.versioning.targetframeworkattribute\(v=vs.110\).aspx) n’est pas appliqué au niveau de l’assembly sont automatiquement exécutées à l’aide de la sémantique (Quirks) du .NET Framework 4.0. Pour garantir une haute qualité, il est recommandé d’attribuer explicitement à tous les fichiers binaires un TargetFrameworkAttribute indiquant la version du .NET Framework avec laquelle ils ont été créés. Si vous utilisez un moniker de Framework cible dans un fichier projet, MSBuild applique automatiquement un TargetFrameworkAttribute.|  
|Suggestion|Un [attribut de Framework cible](https://msdn.microsoft.com/library/system.runtime.versioning.targetframeworkattribute\(v=vs.110\).aspx) doit être fourni, soit en ajoutant directement l’attribut à l’assembly, soit en spécifiant une version cible de Framework dans le [fichier projet ou par le biais de la page de propriétés du projet dans Visual Studio](http://blogs.msdn.com/b/visualstudio/archive/2010/05/19/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework.aspx).|  
|Portée|Majeur|  
|Version|4.5|  
|Type|Exécution|  
|Analyseurs|CD0013|  
  
<a name="diagnostic14"></a>   
## <a name="14-no-longer-able-to-set-enableviewstatemac-to-false"></a>14 : Il n’est plus possible de définir EnableViewStateMac sur false  
  
|||  
|-|-|  
|Détails|ASP.NET ne permet plus aux développeurs de spécifier `<pages enableViewStateMac="false"/>` ou `<@Page EnableViewStateMac="false" %>`. Le code d'authentification de message (code MAC) de l'état d'affichage est à présent appliqué à toutes les demandes avec état d'affichage intégré. Seules les applications qui définissent explicitement la propriété EnableViewStateMac sur false sont affectées.|  
|Suggestion|Vous devez supposer que EnableViewStateMac a la valeur true. Les erreurs MAC résultantes doivent être résolues (comme expliqué dans [cette aide](https://support.microsoft.com/kb/2915218), qui contient plusieurs résolutions en fonction de ce qui provoque les erreurs MAC).|  
|Portée|Majeur|  
|Version|4.5.2|  
|Type|Exécution|  
|Analyseurs|CD0014|  
  
<a name="diagnostic18"></a>   
## <a name="18-blockingcollectionttrytakefromany-does-not-throw-anymore"></a>18 : BlockingCollection\<T>.TryTakeFromAny ne lève plus d’exceptions  
  
|||  
|-|-|  
|Détails|Si l’une des collections d’entrée est marquée comme terminée, `BlockingCollection<T>.TryTakeFromAny(BlockingCollection<T>[], T)` ne retourne plus -1, et `BlockingCollection<T>.TakeFromAny` ne lève plus d’exceptions. Cette modification permet d'utiliser des collections lorsque l'une est vide ou terminée, alors que l'autre comporte toujours des éléments pouvant être récupérés.|  
|Suggestion|Si vous utilisiez TryTakeFromAny pour retourner -1 ou TakeFromAny pour lever des exceptions à des fins de flux de contrôle, dans le contexte d’une collection bloquante terminée, ce code doit à présent être modifié pour utiliser `.Any(b => b.IsCompleted)` de manière à détecter cette condition.|  
|Portée|Mineur|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%29?displayProperty=fullName><br /><br /> <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%29?displayProperty=fullName><br /><br /> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.Int32%29?displayProperty=fullName><br /><br /> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.TimeSpan%29?displayProperty=fullName>|  
|Analyseurs|CD0018A<br /><br /> CD0018B|  
  
<a name="diagnostic19"></a>   
## <a name="19-xmlschemaexception-now-sets-line-positions-properly"></a>19 : XmlSchemaException définit désormais correctement les positions de ligne  
  
|||  
|-|-|  
|Détails|Si la valeur LoadOptions.SetLineInfo est passée à la méthode Load et qu’une erreur de validation se produit, les propriétés XmlSchemaException.LineNumber et XmlSchemaException.LinePosition contiennent désormais des informations de ligne.|  
|Suggestion|Le code de gestion des exceptions qui suppose que XmlSchemaException.LineNumber et XmlSchemaException.LinePosition ne seront pas définis doit être modifié, car ces propriétés seront maintenant définies correctement lorsque SetLineInfo sera utilisé lors du chargement du code XML.|  
|Portée|Limité|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Xml.Linq.LoadOptions?displayProperty=fullName>|  
|Analyseurs|CD0019|  
  
<a name="diagnostic20"></a>   
## <a name="20-systemactivities-is-now-aptca"></a>20 : System.Activities est désormais APTCA  
  
|||  
|-|-|  
|Détails|L’assembly est marqué avec l’attribut AllowPartiallyTrustedCallersAttribute.|  
|Suggestion|Les classes dérivées ne peuvent pas être marquées avec l’objet SecurityCriticalAttribute. Auparavant, les types dérivés devaient être marqués avec l’objet SecurityCriticalAttribute. Toutefois, cette modification ne doit pas avoir d'impact réel.|  
|Portée|Limité|  
|Version|4.5|  
|Type|Exécution|  
|Analyseurs|CD0020|  
  
<a name="diagnostic21"></a>   
## <a name="21-workflow-30-types-are-obsolete"></a>21 : Les types WorkFlow 3.0 sont obsolètes  
  
|||  
|-|-|  
|Détails|Les API WWF (Windows Workflow Foundation) 3.0 (celles de l’espace de noms System.Workflow) sont désormais obsolètes.|  
|Suggestion|Les nouvelles API de WWF 4.0 (celles de System.Activities) doivent être utilisées à la place. Vous pouvez consulter un exemple d’utilisation des nouvelles API [ici](https://msdn.microsoft.com/library/jj205427.aspx) et obtenir une aide [ici](http://blogs.msdn.com/b/workflowteam/archive/2012/02/08/deprecatingwf3.aspx). Étant donné que les API WWF 3.0 sont toujours prises en charge, vous pouvez également les utiliser et éviter l’avertissement au moment de la génération en le supprimant ou en utilisant un compilateur plus ancien.|  
|Portée|Majeur|  
|Version|4.5|  
|Type|Reciblage|  
|Analyseurs|CD0021|  
  
<a name="diagnostic22"></a>   
## <a name="22-some-workflow-drag-and-drop-apis-are-obsolete"></a>22 : Certaines API WorkFlow de glisser-déplacer sont obsolètes  
  
|||  
|-|-|  
|Détails|Cette API WorkFlow de glisser-déplacer est obsolète et génère des avertissements de compilateur si l’application est régénérée avec la version 4.5.|  
|Suggestion|Utilisez à la place les nouvelles API [DragDropHelper](https://msdn.microsoft.com/library/system.activities.presentation.dragdrophelper\(v=vs.110\).aspx) qui prennent en charge les opérations avec plusieurs objets. Vous pouvez également supprimer les avertissements de génération ou les éviter en utilisant un compilateur plus ancien. Ces API sont toujours prises en charge.|  
|Portée|Mineur|  
|Version|4.5|  
|Type|Reciblage|  
|API affectées|<xref:System.Activities.Presentation.DragDropHelper.DoDragMove%28System.Activities.Presentation.WorkflowViewElement%2CSystem.Windows.Point%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView%28System.Windows.DragEventArgs%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem%28System.Windows.DragEventArgs%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject%28System.Windows.DependencyObject%2CSystem.Windows.DragEventArgs%2CSystem.Activities.Presentation.EditingContext%29?displayProperty=fullName>|  
|Analyseurs|CD0022|  
  
<a name="diagnostic23"></a>   
## <a name="23-new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a>23 : Les nouvelles surcharges (ambiguës) Dispatcher.Invoke peuvent entraîner un comportement différent  
  
|||  
|-|-|  
|Détails|Le .NET Framework 4.5 comprend de nouvelles surcharges pour Dispatcher.Invoke qui incluent un paramètre de type System.Action. Lorsque le code existant est recompilé, les compilateurs peuvent résoudre les appels aux méthodes Dispatcher.Invoke dotées d’un paramètre Delegate comme des appels aux méthodes Dispatcher.Invoke ayant un paramètre System.Action. Si un appel à une surcharge Dispatcher.Invoke avec un paramètre Delegate est résolu comme un appel à une surcharge Dispatcher.Invoke avec un paramètre System.Action, les différences de comportement suivantes peuvent survenir :<br /><br /> Si une exception est levée, les événements Dispatcher.UnhandledExceptionFilter et Dispatcher.UnhandledException ne sont pas déclenchés. Les exceptions sont gérées par l’événement UnobservedTaskException.<br /><br /> Les appels à certains membres, comme DispatcherOperation.Result, sont bloqués jusqu’à ce que l’opération soit terminée.|  
|Suggestion|Pour éviter toute ambiguïté (et d’éventuelles différences au niveau de la gestion des exceptions et du blocage des comportements), le code Dispatcher.Invoke appelant peut passer un object[] vide en tant que deuxième paramètre à l’appel Invoke de manière à garantir la résolution de la surcharge de méthode .NET 4.0.|  
|Portée|Mineur|  
|Version|4.5|  
|Type|Reciblage|  
|API affectées|<xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.TimeSpan%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.TimeSpan%2CSystem.Windows.Threading.DispatcherPriority%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.Windows.Threading.DispatcherPriority%2CSystem.Object%5B%5D%29?displayProperty=fullName>|  
|Analyseurs|CD0023|  
  
<a name="diagnostic24"></a>   
## <a name="24-encoderparameter-ctor-is-obsolete"></a>24 : Le constructeur EncoderParameter est obsolète  
  
|||  
|-|-|  
|Détails|Le constructeur `EncoderParameter.EncoderParameter(Encoder, Int32, Int32, Int32)` est désormais obsolète et génère des avertissements quand il est utilisé.|  
|Suggestion|Même si le constructeur `EncoderParameter.EncoderParameter(Encoder, Int32, Int32, Int32)` continue de fonctionner, le constructeur suivant doit être utilisé à sa place pour éviter l’avertissement de génération indiquant qu’il est obsolète, lors de la recompilation du code avec les outils .NET 4.5 : [EncoderParameter.EncoderParameter(Encoder, Int32, EncoderParameterValueType, IntPtr)](https://msdn.microsoft.com/library/hh875096\(v=vs.110\).aspx).|  
|Portée|Mineur|  
|Version|4.5|  
|Type|Reciblage|  
|API affectées|<xref:System.Drawing.Imaging.EncoderParameter.%23ctor%28System.Drawing.Imaging.Encoder%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>|  
|Analyseurs|CD0024|  
  
<a name="diagnostic26"></a>   
## <a name="26-change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>26 : Changement de comportement des méthodes Task.WaitAll avec des arguments timeout  
  
|||  
|-|-|  
|Détails|Le comportement Task.WaitAll est désormais plus cohérent dans le .NET 4.5.<br /><br /> Dans le .NET Framework 4, le comportement de ces méthodes n’était pas cohérent. Lorsque le délai d’attente expirait, si une ou plusieurs tâches étaient terminées ou annulées avant l’appel de la méthode, la méthode levait une exception AggregateException. Lorsque le délai d’attente expirait, si aucune tâche n’était terminée ou annulée avant l’appel de la méthode alors qu’une ou plusieurs tâches adoptaient ces états après l’appel de la méthode, la méthode retournait la valeur false.<br />Dans le .NET Framework 4.5, ces surcharges de méthode retournent désormais la valeur false si des tâches sont toujours en cours d’exécution quand l’intervalle de délai d’attente expire, et elles ne lèvent une exception AggregateException que si une tâche d’entrée a été annulée (que cette annulation soit intervenue avant ou après l’appel de méthode) et qu’une autre tâche n’est pas en cours d’exécution.|  
|Suggestion|Si une exception AggregateException a été interceptée dans le but de détecter une tâche ayant été annulée avant l’appel de WaitAll, ce code doit procéder à la même détection via la propriété IsCanceled (par exemple, .Any(t => t.IsCanceled)), puisque le .NET 4.6 ne lève une exception que si toutes les tâches attendues sont terminées avant le délai d’expiration.|  
|Portée|Mineur|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.Int32%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.Int32%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.TimeSpan%29?displayProperty=fullName>|  
|Analyseurs|CD0026|  
  
<a name="diagnostic27"></a>   
## <a name="27-change-in-behavior-in-data-definition-language-ddl-apis"></a>27 : Changement de comportement des API DDL (Data Definition Language)  
  
|||  
|-|-|  
|Détails|Le comportement des API DDL lors de la spécification d’AttachDBFilename a été modifié de la manière suivante :<br /><br /> Les chaînes de connexion n’ont pas besoin de spécifier de valeur Initial Catalog. Auparavant, AttatchDBFilename et Initial Catalog étaient nécessaires.<br /><br /> Si AttatchDBFilename et Initial Catalog sont spécifiés et qu’un fichier MDF donné existe, la méthode ObjectContext.DatabaseExists retourne true. Avant, elle retournait false.<br /><br /> Si AttatchDBFilename et Initial Catalog sont spécifiés et qu’un fichier MDF donné existe, l’appel de la méthode ObjectContext.DeleteDatabase a pour effet de supprimer les fichiers.<br /><br /> Si ObjectContext.DeleteDatabase est appelé lorsque la chaîne de connexion spécifie une valeur AttachDBFilename avec un fichier MDF qui n’existe pas et un Initial Catalog qui n’existe pas non plus, la méthode lève une exception InvalidOperationException. Avant, elle levait une exception SqlException.|  
|Suggestion|Ces modifications facilitent la création d'outils et d'applications qui utilisent les API DDL. Elles peuvent avoir une incidence sur la compatibilité des applications dans les scénarios suivants :<br /><br /> L’utilisateur écrit du code qui exécute directement une commande DROP DATABASE au lieu d’appeler ObjectContext.DeleteDatabase si ObjectContext.DatabaseExists retourne la valeur true. Ce comportement altère le code existant si la base de données n'est pas liée mais que le fichier MDF existe.<br /><br /> L’utilisateur écrit du code qui s’attend à ce que la méthode ObjectContext.DeleteDatabase lève une exception SqlException plutôt qu’une exception InvalidOperationException lorsque l’Initial Catalog et le fichier MDF n’existent pas.|  
|Portée|Mineur|  
|Version|4.5|  
|Type|Exécution|  
|Analyseurs|CD0027|  
  
<a name="diagnostic28"></a>   
## <a name="28-machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>28 : MachineKey.Encode et MachineKey.Decode sont désormais obsolètes  
  
|||  
|-|-|  
|Détails|Ces méthodes sont désormais obsolètes. La compilation du code qui appelle ces méthodes génère un avertissement du compilateur.|  
|Suggestion|Les alternatives recommandées sont [MachineKey.Protect](https://msdn.microsoft.com/library/system.web.security.machinekey.protect\(v=vs.110\).aspx) et [MachineKey.Unprotect](https://msdn.microsoft.com/library/system.web.security.machinekey.unprotect\(v=vs.110\).aspx). Vous pouvez également supprimer les avertissements de génération ou les éviter en utilisant un compilateur plus ancien. Ces API sont toujours prises en charge.|  
|Portée|Mineur|  
|Version|4.5|  
|Type|Reciblage|  
|API affectées|<xref:System.Web.Security.MachineKey.Decode%28System.String%2CSystem.Web.Security.MachineKeyProtection%29?displayProperty=fullName><br /><br /> <xref:System.Web.Security.MachineKey.Encode%28System.Byte%5B%5D%2CSystem.Web.Security.MachineKeyProtection%29?displayProperty=fullName>|  
|Analyseurs|CD0028|  
  
<a name="diagnostic29"></a>   
## <a name="29-the-replace-method-in-odata-urls-is-disabled-by-default"></a>29 : La méthode Replace est désactivée par défaut dans les URL OData  
  
|||  
|-|-|  
|Détails|À compter de la version 4.5 du .NET Framework, la méthode Replace des URL OData est désactivée par défaut. Quand la méthode Replace OData est désactivée (ce qui est désormais le cas par défaut), toutes les demandes utilisateur, y compris les fonctions de remplacement (qui sont rares) échouent.|  
|Suggestion|Si la méthode Replace est nécessaire (ce qui est rare), elle peut être réactivée via les [paramètres de configuration](https://msdn.microsoft.com/library/system.data.services.configuration.dataservicesfeaturessection.replacefunction.aspx). Toutefois, l’activation d’une méthode Replace peut créer des failles de sécurité et ne doit donc être utilisée qu’après un examen minutieux.|  
|Portée|Limité|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Data.Services.DataService%601?displayProperty=fullName>|  
|Analyseurs|CD0029|  
  
<a name="diagnostic30"></a>   
## <a name="30-systemservicemodelwebwebservicehost-object-no-longer-adds-a-default-endpoint"></a>30 : L’objet System.ServiceModel.Web.WebServiceHost n’ajoute plus de point de terminaison par défaut  
  
|||  
|-|-|  
|Détails|L’objet System.ServiceModel.Web.WebServiceHost n’ajoute plus de point de terminaison par défaut si un point de terminaison explicite a été ajouté par le code de l’application.|  
|Suggestion|Si les utilisateurs s’attendent à pouvoir se connecter à un point de terminaison par défaut alors que d’autres points de terminaison explicites ont été ajoutés à WebServiceHost, les points de terminaison par défaut doivent également être ajoutés explicitement (à l’aide d’AddDefaultEndpoints).|  
|Portée|Mineur|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.ServiceModel.Description.ServiceEndpoint%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%2CSystem.Uri%29?displayProperty=fullName>|  
|Analyseurs|CD0030A<br /><br /> CD0030B|  
  
<a name="diagnostic31"></a>   
## <a name="31-eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>31 : Les implémentations d’EventSource.WriteEvent doivent passer à WriteEvent les mêmes paramètres qu’il a reçus (plus l’ID)  
  
|||  
|-|-|  
|Détails|Le runtime applique à présent le contrat qui stipule ce qui suit : une classe dérivée d’EventSource qui définit une méthode d’événement ETW doit appeler la méthode EventSource.WriteEvent de la classe de base avec l’ID d’événement, suivi des mêmes arguments que ceux passés à la méthode d’événement ETW.|  
|Suggestion|Une exception IndexOutOfRangeException est levée si un EventListener lit des données EventSource dans un processus pour une source d’événements qui ne respecte pas ce contrat.|  
|Portée|Mineur|  
|Version|4.5.1|  
|Type|Exécution|  
|Analyseurs|CD0031|  
  
<a name="diagnostic32"></a>   
## <a name="32-minfreememorypercentagetoactiveservice-is-now-respected"></a>32 : Le paramètre MinFreeMemoryPercentageToActiveService est désormais pris en compte  
  
|||  
|-|-|  
|Détails|Ce paramètre détermine la mémoire minimale devant être disponible sur le serveur avant l’activation d’un service WCF. Il est conçu pour éviter les exceptions OutOfMemoryException. Dans le .NET Framework 4.5, ce paramètre était sans effet. Dans le .NET Framework 4.5.1, ce paramètre est pris en compte.|  
|Suggestion|Une exception se produit si la mémoire disponible sur le serveur web est inférieure au pourcentage défini par le paramètre de configuration. Certains services WCF qui ont réussi à démarrer et à s'exécuter dans un environnement où la mémoire est limitée risquent à présent d'échouer.|  
|Portée|Mineur|  
|Version|4.5.1|  
|Type|Exécution|  
|Analyseurs|CD0032|  
  
<a name="diagnostic33"></a>   
## <a name="33-xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a>33 : L’extension d’entité DTD de XmlTextReader est limitée à 10 000 000 caractères.  
  
|||  
|-|-|  
|Détails|L’extension d’entité DTD est désormais limitée à 10 000 000 caractères. Le chargement des fichiers XML sans extension d'entité DTD ou avec une extension d'entité DTD limitée reste inchangé. Les fichiers avec des entités DTD qui s'étendent à plus de 10 000 000 caractères ne se chargent pas et lèvent désormais une exception.|  
|Suggestion|Si la limite de l’extension d’entité DTD n’est pas suffisante, la valeur peut être substituée par la propriété [XmlReaderSettings.MaxCharactersFromEntities](https://msdn.microsoft.com/library/system.xml.xmlreadersettings.maxcharactersfromentities%28v=vs.110%29.aspx). Un XmlReaderSettings avec la valeur MaxCharactersFromEntity appropriée peut être passé à [XmlReader.Create](https://msdn.microsoft.com/library/System.Xml.XmlReader.Create\(v=vs.110\).aspx)|  
|Portée|Limité|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Xml.XmlTextReader.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%2CSystem.Xml.XmlNodeType%2CSystem.Xml.XmlParserContext%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.TextReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.TextReader%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.Stream%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.TextReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.TextReader%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.Xml.XmlNodeType%2CSystem.Xml.XmlParserContext%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader?displayProperty=fullName>|  
|Analyseurs|CD0033|  
  
<a name="diagnostic35"></a>   
## <a name="35-xslt-style-sheet-exception-message-changed"></a>35 : Le message de l’exception relative aux feuilles de style XSLT a été modifié  
  
|||  
|-|-|  
|Détails|Dans le .NET Framework 4.5, lorsqu’un fichier XSLT est trop complexe, le texte du message d’erreur est le suivant : « La feuille de style est trop complexe. ». Dans les versions antérieures, le message d'erreur était « Erreur de compilation XSLT. ». Le code d'application qui dépend du texte du message d'erreur ne fonctionne plus. Toutefois, comme les types d’exception restent les mêmes, cette modification ne devrait pas avoir d’impact réel.|  
|Suggestion|Mettez à jour le code d’application qui dépend du message d’exception de cette condition d’erreur pour qu’il attende le nouveau message, ou (encore mieux) mettez à jour le code pour qu’il dépende uniquement du type d’exception ([XsltException](https://msdn.microsoft.com/library/system.xml.xsl.xsltexception\(v=vs.110\).aspx)), qui n’a pas changé.|  
|Portée|Limité|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Reflection.MethodInfo%2CSystem.Byte%5B%5D%2CSystem.Type%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.String%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XPath.IXPathNavigable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XPath.IXPathNavigable%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XmlReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XmlReader%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName>|  
|Analyseurs|CD0035|  
  
<a name="diagnostic36"></a>   
## <a name="36-wf-serializes-expressionsliteralt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>36 : WF sérialise les objets DateTimes Expressions.Literal\<T> différemment à présent (il arrête les analyseurs XAML personnalisés)  
  
|||  
|-|-|  
|Détails|L’objet [ValueSerializer](https://msdn.microsoft.com/library/system.windows.markup.valueserializer\(v=vs.110\).aspx) associé convertit un objet DateTime ou DateTimeOffset, dont les composants Second et Millisecond sont différents de zéro et (pour une valeur DateTime) dont la propriété DateTime.Kind n’est pas Unspecified, en une syntaxe d’élément de propriété au lieu d’une chaîne. Cette modification permet aux valeurs DateTime et DateTimeOffset de faire l’objet d’un aller-retour. Les analyseurs XAML personnalisés qui supposent que l'entrée XAML figure dans la syntaxe d'attribut ne fonctionnent pas correctement.|  
|Suggestion|Cette modification permet aux valeurs DateTime et DateTimeOffset de faire l’objet d’un aller-retour. Les analyseurs XAML personnalisés qui supposent que l'entrée XAML figure dans la syntaxe d'attribut ne fonctionnent pas correctement.|  
|Portée|Limité|  
|Version|4.5|  
|Type|Exécution|  
|Analyseurs|CD0036|  
  
<a name="diagnostic37"></a>   
## <a name="37-new-enum-values-in-wpfs-pagerangeselection"></a>37 : Nouvelles valeurs enum dans le PageRangeSelection de WPF  
  
|||  
|-|-|  
|Détails|Deux nouveaux membres (CurrentPage et SelectedPage) ont été ajoutés à l’énumération [PageRangeSelection](https://msdn.microsoft.com/library/system.windows.controls.pagerangeselection\(v=vs.110\).aspx).|  
|Suggestion|Dans la plupart des cas, ces modifications n’affectent pas le code utilisateur. Le code qui dépend d’un certain nombre d’éléments existants dans les appels Enum.GetNames et Enum.GetValues du type PageRangeSelection doit cependant être modifié.|  
|Portée|Limité|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName>|  
|Analyseurs|CD0037|  
  
<a name="diagnostic38"></a>   
## <a name="38-wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>38 : Le DispatcherSynchronizationContext.CreateCopy WPF retourne à présent une nouvelle copie au lieu de l’instance actuelle  
  
|||  
|-|-|  
|Détails|Dans le .NET Framework 4, DispatcherSynchronizationContext.CreateCopy() retournait une référence à l’instance actuelle, principalement pour optimiser les performances. Dans le .NET Framework 4.5, il retourne une nouvelle instance, ce qui permet, pour la première fois, de conclure que les références égales indiquent que le thread en cours d’exécution se trouve dans le bon contexte de synchronisation.  Il est peu probable que le code qui vérifie l’identité de ces références soit affecté. Cependant, en raison de cette modification, le code qui appelle DispatcherSynchronizationContext.CreateCopy doit être testé dans le cadre de la migration vers le .NET Framework 4.5 ou version ultérieure.|  
|Suggestion|N’oubliez pas que DispatcherSynchronizationContext.CreateCopy() retourne désormais un nouvel objet SynchronizationContext.  Avant, le code qui utilisait l’équivalence des références générées de cette manière ne vérifiait pas réellement si le contexte était approprié. À présent, avec le .NET 4.5 et ultérieur, le contexte est bien vérifié.  Bien que cela soit peu susceptible de provoquer des problèmes, l’utilisation des chemins de code concernés doit suffire à déterminer si cela peut poser un problème.|  
|Portée|Mineur|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=fullName>|  
|Analyseurs|CD0038|  
  
<a name="diagnostic39"></a>   
## <a name="39-systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>39 : System.Threading.Tasks.Task ne lève plus d’exception ObjectDisposedException après la suppression de l’objet  
  
|||  
|-|-|  
|Détails|Les méthodes System.Threading.Tasks.Task (sauf Task.IAsyncResult.AsyncWaitHandle) ne lèvent plus d’exception ObjectDisposedException après la suppression de l’objet.<br />Cette modification prend en charge l'utilisation des tâches mises en cache. Par exemple, une méthode peut retourner une tâche mise en cache pour représenter une opération déjà terminée au lieu d'allouer une nouvelle tâche. Cette opération était impossible dans les versions précédentes du .NET Framework, car tout consommateur de la tâche pouvait la supprimer, ce qui la rendait inutilisable.|  
|Suggestion|N’oubliez pas que les méthodes Task peuvent ne plus lever d’exceptions ObjectDisposedExceptions lorsque l’objet est supprimé. Si une application dépendait de cette exception pour savoir qu’une tâche avait été supprimée, elle doit être mise à jour pour vérifier explicitement l’état de la tâche à l’aide de [Task.Status](https://msdn.microsoft.com/library/system.threading.tasks.task.status\(v=vs.110\).aspx).|  
|Portée|Mineur|  
|Version|4.5|  
|Type|Exécution|  
|Analyseurs|CD0039|  
  
<a name="diagnostic40"></a>   
## <a name="40-different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>40 : Gestion des exceptions différente pour les méthodes ObjectContext.CreateDatabase et DbProviderServices.CreateDatabase  
  
|||  
|-|-|  
|Détails|À compter de la version 4.5 du .NET, en cas d’échec de la création d’une base de données, les méthodes `CreateDatabase` tentent de supprimer la base de données vide. Si cette opération réussit, l’exception `SQLException` d’origine est propagée (au lieu de l’exception `InvalidOperationException` qui était systématiquement levée dans le .NET 4.0)|  
|Suggestion|À présent, lorsque vous interceptez une exception InvalidOperationException lors de l’exécution d’ObjectContext.CreateDatabase ou DbProviderServices.CreateDatabase, les exceptions SQLException doivent également être interceptées.|  
|Portée|Mineur|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Data.Common.DbProviderServices.CreateDatabase%28System.Data.Common.DbConnection%2CSystem.Nullable%7BSystem.Int32%7D%2CSystem.Data.Metadata.Edm.StoreItemCollection%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName>|  
|Analyseurs|CD0040|  
  
<a name="diagnostic41"></a>   
## <a name="41-objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>41 : ObjectContext.Translate et ObjectContext.ExecuteStoreQuery prennent désormais en charge le type enum  
  
|||  
|-|-|  
|Détails|Dans le .NET 4.0, le paramètre générique `T` des méthodes `ObjectContext.Translate` et `ObjectContext.ExecuteStoreQuery` ne pouvait pas être une énumération. Ce scénario est désormais pris en charge.|  
|Suggestion|Si Translate ou ExecuteStoreQuery était appelé sur un type enum dans le .NET 4.0, la valeur « 0 » était retournée. Si ce comportement était celui souhaité, les appels devaient être remplacés par une constante 0 (ou l’équivalent enum de celle-ci).|  
|Portée|Limité|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601%28System.String%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601%28System.String%2CSystem.String%2CSystem.Data.Objects.MergeOption%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.Translate%60%601%28System.Data.Common.DbDataReader%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.Translate%60%601%28System.Data.Common.DbDataReader%2CSystem.String%2CSystem.Data.Objects.MergeOption%29?displayProperty=fullName>|  
|Analyseurs|CD0041|  
  
<a name="diagnostic42"></a>   
## <a name="42-enumerableemptytresult-always-returns-cached-instance"></a>42 : Enumerable.Empty\<TResult> retourne toujours une instance mise en cache  
  
|||  
|-|-|  
|Détails|À compter de la version 4.5 du .NET, `Enumerable.Empty` retourne toujours une instance interne `IEnumerable<T>` mise en cache.<br /><br /> Auparavant, `Enumerable.Empty` mettait en cache un `IEnumerable<T>` vide lors de l’appel de l’API, ce qui signifiait que dans certaines conditions, lorsque `Enumerable.Empty` était appelé rapidement et simultanément, différentes instances du type pouvaient être retournées pour différents appels à l’API.|  
|Suggestion|Étant donné que l’ancien comportement était non déterministe, il est peu probable que le code en dépende. Toutefois, dans le cas peu probable où des énumérables vides sont comparés et supposés être parfois inégaux, vous devez créer des tableaux vides explicites (`new T[0]`) au lieu d’utiliser `Enumerable.Empty`.|  
|Portée|Limité|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=fullName>|  
|Analyseurs|CD0042|  
  
<a name="diagnostic43"></a>   
## <a name="43-httprequestcontentencoding-property-prohibits-utf7"></a>43 :La propriété HttpRequest.ContentEncoding interdit UTF7  
  
|||  
|-|-|  
|Détails|À compter de la version 4.5 du .NET Framework, l’encodage UTF-7 est interdit dans le corps des HttpRequests. Les données des applications qui dépendent des données UTF-7 entrantes ne seront pas décodées correctement dans certains cas.|  
|Suggestion|Dans l’idéal, les applications doivent être mises à jour pour ne pas utiliser l’encodage UTF-7 dans les HttpRequests. Vous pouvez aussi restaurer le comportement hérité à l’aide de l’attribut `aspnet:AllowUtf7RequestContentEncoding` de l’élément [appSettings](https://msdn.microsoft.com/library/hh975440\(v=vs.110\).aspx).|  
|Portée|Limité|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Web.HttpRequest.ContentEncoding?displayProperty=fullName>|  
|Analyseurs|CD0043|  
  
<a name="diagnostic44"></a>   
## <a name="44-httputilityjavascriptstringencode-escapes-ampersand"></a>44 : HttpUtility.JavaScriptStringEncode échappe le caractère esperluette (&)  
  
|||  
|-|-|  
|Détails|À compter de la version 4.5 du .NET Framework, JavaScriptStringEncode échappe le caractère esperluette (&).|  
|Suggestion|Si votre application dépend du comportement précédent de cette méthode, vous pouvez ajouter un paramètre aspnet:JavaScriptDoNotEncodeAmpersand à l’[élément appSettings ASP.NET](https://msdn.microsoft.com/library/hh975440\(v=vs.110\).aspx) dans votre fichier de configuration.|  
|Portée|Mineur|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Web.HttpUtility.JavaScriptStringEncode%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Web.HttpUtility.JavaScriptStringEncode%28System.String%2CSystem.Boolean%29?displayProperty=fullName>|  
|Analyseurs|CD0044A<br /><br /> CD0044B|  
  
<a name="diagnostic46"></a>   
## <a name="46-eventlistener-truncates-strings-with-embedded-nulls"></a>46 : EventListener tronque les chaînes comportant des valeurs Null incorporées  
  
|||  
|-|-|  
|Détails|EventListener tronque les chaînes comportant des valeurs Null incorporées. Les caractères Null ne sont pas pris en charge par la classe EventSource. Cette modification affecte uniquement les applications qui utilisent EventListener pour lire des données EventSource dans le processus et qui utilisent des caractères Null comme délimiteurs.|  
|Suggestion|Les données EventSource doivent être, si possible, mises à jour pour ne pas utiliser les caractères Null incorporés.|  
|Portée|Limité|  
|Version|4.5.1|  
|Type|Exécution|  
|API affectées|<xref:System.Diagnostics.Tracing.EventListener.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%2CSystem.Diagnostics.Tracing.EventKeywords%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%2CSystem.Diagnostics.Tracing.EventKeywords%2CSystem.Collections.Generic.IDictionary%7BSystem.String%2CSystem.String%7D%29?displayProperty=fullName>|  
|Analyseurs|CD0046|  
  
<a name="diagnostic48"></a>   
## <a name="48-obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>48 : ObsoleteAttribute est exporté à la fois comme ObsoleteAttribute et DeprecatedAttribute dans les scénarios WinMD  
  
|||  
|-|-|  
|Détails|Quand vous créez une bibliothèque de métadonnées Windows (fichier .winmd), l’attribut ObsoleteAttribute est exporté à la fois en tant qu’ObsoleteAttribute et que Windows.Foundation.DeprecatedAttribute.|  
|Suggestion|La recompilation de code source existant qui utilise l’attribut ObsoleteAttribute peut générer des avertissements quand ce code est consommé à partir de C++/CX ou JavaScript.<br /><br /> Nous déconseillons d’appliquer à la fois ObsoleteAttribute et Windows.Foundation.DeprecatedAttribute au code d’assemblys managés, car cela peut générer des avertissements de génération.|  
|Portée|Limité|  
|Version|4.5.1|  
|Type|Reciblage|  
|Analyseurs|CD0048A<br /><br /> CD0048B|  
  
<a name="diagnostic49"></a>   
## <a name="49-resolveassemblyreference-task-now-warns-on-dependencies-with-the-wrong-architecture"></a>49 : La tâche ResolveAssemblyReference génère désormais un avertissement quand une dépendance n’a pas la bonne architecture  
  
|||  
|-|-|  
|Détails|La tâche émet un avertissement, MSB3270, qui indique qu’une référence ou l’une de ses dépendances ne correspond pas à l’architecture de l’application. Cette situation peut se produire, par exemple, si une application qui a été compilée avec l’option anycpu inclut une référence x86. Ainsi, l'application peut échouer au moment de l'exécution (si l'application est déployée en tant que processus x64 dans notre exemple).|  
|Suggestion|Deux domaines sont impactés :<br /><br /> La recompilation génère des avertissements qui n'étaient pas apparus quand l'application avait été compilée sous une version antérieure de MSBuild. En revanche, étant donné que l'avertissement identifie une source potentielle d'échec du runtime, vous devez l'examiner et le traiter.<br /><br /> Si les avertissements sont considérés comme des erreurs, la compilation de l'application échouera.|  
|Portée|Mineur|  
|Version|4.5.1|  
|Type|Reciblage|  
|Analyseurs|CD0049|  
  
<a name="diagnostic51"></a>   
## <a name="51-wpf-textbox-defaults-to-undo-limit-of-100"></a>51 : Le nombre maximal d’annulations d’opérations pour une zone de texte WPF est de 100 par défaut  
  
|||  
|-|-|  
|Détails|Dans le .NET 4.5, le nombre maximal d’annulations d’opérations pour une zone de texte WPF est de 100 par défaut (dans le .NET 4.0, ce nombre était illimité).|  
|Suggestion|Si ce nombre n’est pas suffisant, vous pouvez définir explicitement cette valeur à l’aide de la propriété UndoLimit de la zone de texte.|  
|Portée|Limité|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Windows.Controls.TextBox?displayProperty=fullName>|  
|Analyseurs|CD0051|  
  
<a name="diagnostic55"></a>   
## <a name="55-exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a>55 : Les exceptions qui sont levées pendant un traitement non pris en charge dans System.Threading.Tasks.Task ne se propagent plus sur le thread finaliseur  
  
|||  
|-|-|  
|Détails|Comme la classe System.Threading.Tasks.Task représente une opération asynchrone, elle intercepte toutes les exceptions sans gravité qui se produisent pendant le traitement asynchrone. Dans le .NET Framework 4.5, si une exception n’est pas prise en charge et si votre code n’attend jamais la tâche, l’exception ne se propagera plus sur le thread finaliseur et arrêtera le processus pendant l’opération garbage collection. Cette modification améliore la fiabilité des applications qui utilisent la classe Task pour exécuter un traitement asynchrone non pris en charge.|  
|Suggestion|Si une application dépend d’exceptions asynchrones non prises en charge qui se propagent au thread finaliseur, le comportement précédent peut être restauré en fournissant un gestionnaire approprié pour l’événement [TaskScheduler.UnobservedTaskException](https://msdn.microsoft.com/library/system.threading.tasks.taskscheduler.unobservedtaskexception\(v=vs.110\).aspx) ou en définissant un [élément de configuration d’exécution](https://msdn.microsoft.com/library/jj160346%28v=vs.110%29.aspx).|  
|Portée|Limité|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Action%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%60%600%7D%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%60%600%7D%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7B%60%600%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7B%60%600%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Start?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Start%28System.Threading.Tasks.TaskScheduler%29?displayProperty=fullName>|  
|Analyseurs|CD0055|  
  
<a name="diagnostic58"></a>   
## <a name="58-iasyncresultcompletedsynchronously-property-must-be-correct-for-the-resulting-task-to-complete"></a>58 : La propriété IAsyncResult.CompletedSynchronously doit être correctement configurée pour que la tâche résultante puisse se terminer  
  
|||  
|-|-|  
|Détails|Lorsqu’elle appelle TaskFactory.FromAsync, l’implémentation de la propriété IAsyncResult.CompletedSynchronously doit être correctement configurée pour que la tâche résultante puisse se terminer. Autrement dit, la propriété doit retourner la valeur true si, et uniquement si, l’implémentation s’est effectuée de façon synchrone. Auparavant, la propriété n'était pas vérifiée.|  
|Suggestion|Si les implémentations d’IAsyncResult retournent la valeur true pour la propriété CompletedSynchronusly uniquement lorsqu’une tâche se termine de façon synchrone, l’exécution n’est pas arrêtée. Les utilisateurs doivent examiner leurs implémentations d’IAsyncResult afin de vérifier qu’elles évaluent correctement si une tâche se termine de manière synchrone ou non.|  
|Portée|Limité|  
|Version|4.5|  
|Type|Reciblage|  
|API affectées|<xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Threading.Tasks.TaskCreationOptions%2CSystem.Threading.Tasks.TaskScheduler%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Threading.Tasks.TaskCreationOptions%2CSystem.Threading.Tasks.TaskScheduler%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%601%7D%2C%60%600%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%601%7D%2C%60%600%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%602%7D%2C%60%600%2C%60%601%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%602%7D%2C%60%600%2C%60%601%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%603%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%603%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName>|  
|Analyseurs|CD0058|  
  
<a name="diagnostic59"></a>   
## <a name="59-log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>59 : Le nom du fichier journal créé par la méthode ObjectContext.CreateDatabase a été changé pour répondre aux spécifications SQL Server  
  
|||  
|-|-|  
|Détails|Lorsque la méthode CreateDatabase est appelée directement ou en utilisant Code First avec le fournisseur SqlClient et une valeur AttachDBFilename dans la chaîne de connexion, elle crée un fichier journal nommé nom_fichier_log.ldf au lieu de nom_fichier.ldf (où « nom_fichier » correspond au nom du fichier spécifié par la valeur AttachDBFilename). Cette modification améliore le débogage en fournissant un fichier journal dont le nom répond aux spécifications SQL Server.|  
|Suggestion|Si le nom du fichier journal est important pour une application, celle-ci doit être mise à jour pour attendre le format de nom de fichier standard « _log.ldf ».|  
|Portée|Limité|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName>|  
|Analyseurs|CD0059|  
  
<a name="diagnostic60"></a>   
## <a name="60-pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>60 : L’événement Page.LoadComplete n’entraîne plus l’appel d’une liaison de données par le contrôle System.Web.UI.WebControls.EntityDataSource  
  
|||  
|-|-|  
|Détails|L’événement `Page.LoadComplete` n’a plus pour effet d’entraîner l’appel d’une liaison de données par le contrôle System.Web.UI.WebControls.EntityDataSource dans le but de créer, mettre à jour ou supprimer des paramètres. Cette modification supprime un aller-retour superflu vers la base de données, empêche la réinitialisation des valeurs des contrôles et produit un comportement cohérent avec les autres contrôles de données, tels que SqlDataSource et ObjectDataSource. Elle produit un comportement différent dans le cas peu probable où les applications dépendraient de l'appel de la liaison de données dans l'événement `Page.LoadComplete`.|  
|Suggestion|Si une liaison de données est nécessaire, appelez manuellement la méthode databind dans un événement situé plus haut dans la publication (postback).|  
|Portée|Limité|  
|Version|4.5|  
|Type|Exécution|  
|Analyseurs|CD0060|  
  
<a name="diagnostic61"></a>   
## <a name="61-webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a>61 : WebUtility.HtmlDecode ne décode plus les séquences d’entrée non valides  
  
|||  
|-|-|  
|Détails|Par défaut, les méthodes de décodage ne décodent plus une séquence d'entrée non valide en une chaîne UTF-16 non valide. Au lieu de cela, elles retournent l'entrée d'origine.|  
|Suggestion|Le changement lié à la sortie du décodeur doit importer uniquement si vous stockez des données binaires à la place de données UTF-16 dans les chaînes. Pour contrôler explicitement ce comportement, affectez à l’attribut `aspnet:AllowRelaxedUnicodeDecoding` de l’élément [appSettings](https://msdn.microsoft.com/library/ms228154\(v=vs.110\).aspx) la valeur true pour activer le comportement hérité, ou la valeur false pour activer le comportement actuel.|  
|Portée|Mineur|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Net.WebUtility.HtmlDecode%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Net.WebUtility.HtmlDecode%28System.String%2CSystem.IO.TextWriter%29?displayProperty=fullName><br /><br /> <xref:System.Net.WebUtility.UrlDecode%28System.String%29?displayProperty=fullName>|  
|Analyseurs|CD0061|  
  
<a name="diagnostic63"></a>   
## <a name="63-apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>63 : Les applications publiées avec ClickOnce qui utilisent un certificat de signature de code SHA-256 peuvent échouer sur Windows 2003  
  
|||  
|-|-|  
|Détails|L'exécutable est signé avec SHA256. Auparavant, il était signé avec SHA1, que le certificat de signature du code ait été SHA-1 ou SHA-256. Cela s'applique à :<br /><br /> Toutes les applications générées avec Visual Studio 2012 ou ultérieur.<br /><br /> Toutes les applications générées avec Visual Studio 2010 ou antérieur en présence de .NET Framework 4.5.<br /><br /> En outre, si .NET Framework 4.5 (ou une version ultérieure) est présent, le manifeste ClickOnce est également signé avec SHA-256 pour les certificats SHA-256, quelle que soit la version du .NET Framework sur laquelle il a été compilé.|  
|Suggestion|Le changement de signature de l’exécutable ClickOnce affecte uniquement les systèmes Windows Server 2003. Vous devez installer le correctif logiciel KB 938397.<br /><br /> Le changement de signature du manifeste avec l'algorithme SHA-256 même quand une application cible .NET Framework 4.0, ou des versions antérieures, présente une dépendance de runtime sur .NET Framework 4.5 ou version ultérieure.|  
|Portée|Limité|  
|Version|4.5-4.6|  
|Type|Reciblage|  
|Analyseurs|CD0063|  
  
<a name="diagnostic68"></a>   
## <a name="68-dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a>68 : DbParameter.Precision et DbParameter.Scale sont désormais des membres virtuels public  
  
|||  
|-|-|  
|Détails|DbParameter.Precision et DbParameter.Scale sont implémentés comme des propriétés virtuelles publiques. Ils remplacent les implémentations d’interface explicites correspondantes que sont DbParameter.IDbDataParameter.Precision et DbParameter.IDbDataParameter.Scale.|  
|Suggestion|Lorsque vous régénérez un fournisseur de base de données ADO.NET, vous devez désormais appliquer le mot clé « override » aux propriétés Precision et Scale. Cette opération est nécessaire uniquement si vous régénérez les composants. Les fichiers binaires existants continueront de fonctionner.|  
|Portée|Mineur|  
|Version|4.5.1|  
|Type|Reciblage|  
|API affectées|<xref:System.Data.Common.DbParameter.Precision?displayProperty=fullName><br /><br /> <xref:System.Data.Common.DbParameter.Scale?displayProperty=fullName>|  
|Analyseurs|CD0068|  
  
<a name="diagnostic73"></a>   
## <a name="73-dataobjectgetdata-now-retrieves-data-as-utf-8"></a>73 : DataObject.GetData récupère maintenant les données au format UTF-8  
  
|||  
|-|-|  
|Détails|Pour les applications qui ciblent le .NET Framework 4 ou qui s’exécutent sur le .NET Framework 4.5.1 ou versions antérieures, DataObject.GetData récupère les données au format HTML sous forme de chaîne ASCII. Ainsi, les caractères non-ASCII (caractères dont les codes ASCII sont supérieurs à 0x7F) sont représentés par deux caractères aléatoires.<br /><br /> Pour les applications qui ciblent le .NET Framework 4.5 ou version ultérieure et qui s’exécutent sur le .NET Framework 4.5.2, `DataObject.GetData` récupère les données au format HTML sous la forme de données UTF-8, qui représentent correctement les caractères supérieurs à 0x7F.|  
|Suggestion|Si vous avez implémenté une solution de contournement pour ce problème de codage des chaînes au format HTML (par exemple, en codant explicitement la chaîne HTML récupérée à partir du Presse-papiers en la transférant à la méthode UTF8Encoding.GetString) et que vous reciblez votre application depuis la version 4 vers la version 4.5, cette solution devrait être supprimée.<br /><br /> Si l’ancien comportement est nécessaire, l’application peut cibler le .NET Framework 4.0 pour l’obtenir.|  
|Portée|Limité|  
|Version|4.5.2|  
|Type|Reciblage|  
|API affectées|<xref:System.Windows.DataObject.GetData%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Windows.DataObject.GetData%28System.String%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Windows.DataObject.GetData%28System.Type%29?displayProperty=fullName>|  
|Analyseurs|CD0073|  
  
<a name="diagnostic75"></a>   
## <a name="75-targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>75 : Dans le domaine d’application par défaut, TargetFrameworkName n’est plus défini sur Null par défaut quand il n’est pas défini explicitement  
  
|||  
|-|-|  
|Détails|Auparavant, TargetFrameworkName était défini sur la valeur Null dans le domaine d’application par défaut quand il n’était pas défini explicitement. À compter de la version 4.6, la valeur par défaut de la propriété TargetFrameworkName du domaine d’application par défaut est dérivée de TargetFrameworkAttribute (si celui-ci est présent). Les domaines d’application autres que ceux par défaut continuent d’hériter leur valeur TargetFrameworkName du domaine d’application par défaut (qui n’aura pas la valeur Null par défaut dans la version 4.6), sauf si cette valeur est substituée explicitement.|  
|Suggestion|Le code doit être mis à jour pour ne pas attendre que `AppDomainSetup.TargetFrameworkName` ait la valeur Null par défaut. Si vous avez besoin que cette propriété continue de prendre la valeur Null, vous pouvez la définir explicitement sur cette valeur.|  
|Portée|Limité|  
|Version|4.6|  
|Type|Exécution|  
|API affectées|<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName>|  
|Analyseurs|CD0075B<br /><br /> CD0075A|  
  
<a name="diagnostic76"></a>   
## <a name="76-x509certificate2tostringbool-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>76 : X509Certificate2.ToString(bool) ne lève plus d’exception quand .NET ne peut pas gérer le certificat  
  
|||  
|-|-|  
|Détails|Avant, cette méthode levait une exception quand la valeur « true » était passée au paramètre verbose alors que des certificats non pris en charge par le .NET Framework étaient installés. À présent, la méthode n’échoue plus et retourne une chaîne valide qui omet les parties inaccessibles du certificat.|  
|Suggestion|Le code qui dépend de X509Certificate2.ToString(bool) doit être mis à jour pour s’attendre à ce que la chaîne retournée omette certaines données du certificat (telles que la clé publique, la clé privée et les extensions), ce qui aurait auparavant entraîné la levée d’une exception par l’API.|  
|Portée|Limité|  
|Version|4.6|  
|Type|Exécution|  
|API affectées|<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString%28System.Boolean%29?displayProperty=fullName>|  
|Analyseurs|CD0076|  
  
<a name="diagnostic77"></a>   
## <a name="77-reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>77 : Les objets de réflexion ne peuvent plus être passés du code managé aux clients DCOM hors processus  
  
|||  
|-|-|  
|Détails|Les objets de réflexion ne peuvent plus être passés du code managé aux clients DCOM hors processus. Les types suivants sont concernés :<br /><br /> Assembly<br /><br /> MemberInfo (et ses types dérivés, y compris FieldInfo, MethodInfo, Type et TypeInfo)<br /><br /> MethodBody<br /><br /> Module<br /><br /> ParameterInfo<br /><br /> Les appels à `IMarshal` pour l’objet retournent `E_NOINTERFACE`.|  
|Suggestion|Mettez à jour le code de marshaling pour utiliser des objets autres que des objets de réflexion.|  
|Portée|Mineur|  
|Version|4.6|  
|Type|Exécution|  
|Analyseurs|CD0077|  
  
<a name="diagnostic78"></a>   
## <a name="78-contentdisposition-datetimes-returns-slightly-different-string"></a>78 : Les DateTime ContentDisposition retournent une chaîne légèrement différente  
  
|||  
|-|-|  
|Détails|À compter de la version 4.6, les représentations sous forme de chaîne des ContentDisposition représentent toujours le composant d’heure d’une valeur DateTime avec deux chiffres. Ce changement a pour but de se conformer aux normes [RFC822](http://www.ietf.org/rfc/rfc0822.txt) et [RFC2822](http://www.ietf.org/rfc/rfc2822.txt). `ContentDisposition.ToString` retourne à présent une chaîne légèrement différente dans la version 4.6, lorsque l’un des éléments d’heure de la disposition est antérieur à 10:00. Notez que les ContentDisposition sont parfois sérialisés lors de leur conversion en chaînes. Pour cette raison, les opérations ToString ContentDisposition, les sérialisations et les appels GetHashCode doivent être examinés.|  
|Suggestion|Ne vous attendez pas à ce que les représentations sous forme de chaîne des ContentDisposition issues de différentes versions du .NET Framework puissent être comparées correctement. Reconvertissez les chaînes en ContentDisposition, si possible, avant d’effectuer une comparaison.|  
|Portée|Mineur|  
|Version|4.6|  
|Type|Exécution|  
|API affectées|<xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=fullName><br /><br /> <xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=fullName>|  
|Analyseurs|CD0078|  
  
<a name="diagnostic82"></a>   
## <a name="82-workflowdesignerload-doesnt-remove-symbol-property"></a>82 : WorkflowDesigner.Load ne supprime pas les propriétés de symbole  
  
|||  
|-|-|  
|Détails|Lorsque vous ciblez le .NET Framework 4.5 dans le Concepteur de flux de travail et chargez un flux de travail 3.5 réhébergé avec la méthode WorkflowDesigner.Load(), une exception XamlDuplicateMemberException est levée quand vous enregistrez le flux de travail.|  
|Suggestion|Ce bogue se produit uniquement lorsque vous reciblez le .NET Framework 4.5 dans le Concepteur de flux de travail. Vous pouvez donc contourner le problème en définissant `WorkflowDesigner.Context.Services.GetService<DesignerConfigurationService>().TargetFrameworkName` sur le .NET Framework 4.0.<br /><br /> Vous pouvez également éviter le problème en utilisant la méthode [WorkflowContext.Load(string)](https://msdn.microsoft.com/library/ee425926\(v=vs.110\).aspx) pour charger le flux de travail, au lieu de [WorkflowDesigner.Load()](https://msdn.microsoft.com/library/ee403482\(v=vs.110\).aspx).|  
|Portée|Majeur|  
|Version|4.5-4.5.2|  
|Type|Reciblage|  
|API affectées|<xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=fullName>|  
|Analyseurs|CD0082|  
  
<a name="diagnostic83"></a>   
## <a name="83-sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>83 : SqlConnection.Open échoue sur Windows 7 si des BSP ou LSP Winsock non IFS sont installés  
  
|||  
|-|-|  
|Détails|SqlConneciton.Open et OpenAsync échouent dans le .NET Framework 4.5 quand des BSP ou LSP Winsock non IFS sont installés sur un ordinateur Windows 7.<br /><br /> Pour déterminer si des BSP ou des LSP non IFS sont installés, utilisez la commande `netsh WinSock Show Catalog` et examinez chaque élément `Winsock Catalog Provider Entry` retourné. Si la valeur des indicateurs de service est définie sur `0x20000`, le fournisseur utilise des gestionnaires IFS ce qui lui permet de fonctionner correctement. Si la valeur `0x20000` n’est pas définie, c’est qu’il s’agit d’un BSP ou d’un LSP non IFS.|  
|Suggestion|Ce bogue a été résolu dans le .NET Framework 4.5.2. Vous pouvez donc l’éviter en mettant à niveau votre version du .NET Framework. Vous pouvez également l’éviter en supprimant tous les LSP Winsock non IFS qui sont installés.|  
|Portée|Mineur|  
|Version|4.5-4.5.2|  
|Type|Exécution|  
|API affectées|<xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=fullName><br /><br /> <xref:System.Data.SqlClient.SqlConnection.OpenAsync%28System.Threading.CancellationToken%29?displayProperty=fullName>|  
|Analyseurs|CD0083|  
  
<a name="diagnostic84"></a>   
## <a name="84-icommandcanexecutechanged-event-behaviour-changed-in-net-45"></a>84 : Le comportement de l’événement ICommand.CanExecuteChanged a été modifié dans le .NET 4.5  
  
|||  
|-|-|  
|Détails|Dans le .NET Framework 4.5, CanExecuteChangedEvent était ignoré, sauf si l’objet qui avait envoyé l’événement était le même que celui qui l’avait déclenché. Ce bogue a été corrigé dans les mises à jour de maintenance du .NET Framework 4.5.|  
|Suggestion|Ce bogue a été résolu dans les versions de maintenance du .NET Framework 4.5. Vous pouvez donc l’éviter en vérifiant que votre .NET Framework est à jour ou en le mettant à niveau vers .NET Framework 4.5.1. Vous pouvez également modifier le code d’application ICommand pour faire en sorte que, lorsqu’il déclenche une commande CanExecuteChanged, l’objet qui envoie l’événement soit le même que celui qui déclenche l’événement.|  
|Portée|Mineur|  
|Version|4.5-4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=fullName>|  
|Analyseurs|CD0084|  
  
<a name="diagnostic85"></a>   
## <a name="85-some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>85 : Certaines API .NET provoquent des exceptions EntryPointNotFoundExceptions de première chance (gérées)  
  
|||  
|-|-|  
|Détails|Dans le .NET Framework 4.5, un petit nombre de méthodes .NET levaient des exceptions EntryPointNotFoundExceptions de première chance. Ces exceptions étaient gérées dans le .NET Framework, mais pouvaient arrêter l’automatisation des tests, car celle-ci ne s’attendait pas à des exceptions de première chance. Ces mêmes API provoquent l’arrêt de certaines exécutions ApiVerifier lorsque HighVersionLie est activé.|  
|Suggestion|Vous pouvez éviter ce problème en effectuant une mise à niveau vers .NET Framework 4.5.1. Vous pouvez aussi mettre à jour le code d’automatisation des tests pour que son exécution ne soit pas arrêtée en cas d’exceptions EntryPointNotFoundExceptions de première chance.|  
|Portée|Limité|  
|Version|4.5-4.5.1|  
|Type|Exécution|  
|API affectées|<xref:System.Diagnostics.Debug.Assert%28System.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%29?displayProperty=fullName>|  
|Analyseurs|CD0085|  
  
<a name="diagnostic86"></a>   
## <a name="86-scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>86 : Le défilement d’un TreeView ou d’une ListBox groupée WPF dans un VirtualizingStackPanel peut provoquer un blocage  
  
|||  
|-|-|  
|Détails|Dans le .NET Framework 4.5, le défilement d’un contrôle TreeView WPF dans un panneau d’empilement virtualisé peut provoquer un blocage si la fenêtre d’affichage comporte des marges (entre les éléments du TreeView, par exemple, ou sur un élément ItemsPresenter). En outre, dans certains cas, des éléments de taille différente dans une même vue peuvent causer une instabilité, même s’il n’y a pas de marges.|  
|Suggestion|Vous pouvez éviter ce problème en effectuant une mise à niveau vers .NET Framework 4.5.1. Vous pouvez également supprimer les marges des collections d’affichage (comme les TreeView) dans les panneaux d’empilement virtualisés, si tous les éléments qu’ils contiennent sont de même taille.|  
|Portée|Majeur|  
|Version|4.5-4.5.1|  
|Type|Exécution|  
|API affectées|<xref:System.Windows.Controls.VirtualizingPanel.SetIsVirtualizing%28System.Windows.DependencyObject%2CSystem.Boolean%29?displayProperty=fullName>|  
|Analyseurs|CD0086<br /><br /> CD0086|  
  
<a name="diagnostic89"></a>   
## <a name="89-typeisassignablefrom-returns-wrong-result-for-generic-variables-with-constraints"></a>89 : Type.IsAssignableFrom retourne un résultat incorrect pour les variables génériques avec contraintes  
  
|||  
|-|-|  
|Détails|Dans le .NET Framework 4.5, Type.IsAssignableFrom retourne systématiquement `false` pour certains types génériques avec contraintes.|  
|Suggestion|Ce problème a été corrigé dans une mise à jour de maintenance. Pour résoudre ce problème, mettez à jour .NET Framework 4.5 ou mettez-le à niveau vers .NET Framework 4.5.1 ou version ultérieure. Vous pouvez également ne pas utiliser d’IsAssignableFrom avec les types génériques qui ont des contraintes sur les paramètres génériques. Vous pouvez utiliser les API de réflexion comme solutions de contournement.|  
|Portée|Mineur|  
|Version|4.5-4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Type.IsAssignableFrom%28System.Type%29?displayProperty=fullName>|  
|Analyseurs|CD0089<br /><br /> CD0089|  
  
<a name="diagnostic91"></a>   
## <a name="91-entityframework-60-loads-very-slowly-in-apps-launched-from-visual-studio"></a>91 : Le chargement d’Entity Framework 6.0 est très lent pour les applications lancées à partir de Visual Studio  
  
|||  
|-|-|  
|Détails|Dans Visual Studio 2013, le lancement d’une application qui utilise Entity Framework 6.0 peut être très long.|  
|Suggestion|Ce problème a été résolu dans EntityFramework 6.0.2. Mettez à jour Entity Framework pour éviter des problèmes de performances.|  
|Portée|Limité|  
|Version|4.5|  
|Type|Exécution|  
|Analyseurs|CD0091|  
  
<a name="diagnostic92"></a>   
## <a name="92-multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>92 : L’espacement de la zone de texte multiligne ASP.NET a été modifié pour l’utilisation d’AntiXSSEncoder  
  
|||  
|-|-|  
|Détails|Dans le .NET Framework 4.0, des lignes supplémentaires étaient insérées dans la zone de texte multiligne lors de la publication (postback), quand vous utilisiez `AntiXSSEncoder`. Dans le .NET Framework 4.5, ces sauts de ligne supplémentaires ne sont pas inclus si l’application web cible .NET 4.5.|  
|Suggestion|Notez que les applications web 4.0 reciblées vers .NET 4.5 peuvent avoir des zones de texte multilignes améliorées qui ne comportent plus de sauts de ligne supplémentaires. Si ce changement n’est pas souhaitable, vous pouvez obtenir l’ancien comportement dans le .NET Framework 4.5 en ciblant le .NET Framework 4.0.|  
|Portée|Mineur|  
|Version|4.5|  
|Type|Reciblage|  
|Analyseurs|CD0092|  
  
<a name="diagnostic95"></a>   
## <a name="95-concurrentqueuettrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>95 : ConcurrentQueue\<T>.TryPeek peut retourner une valeur Null erronée via son paramètre de sortie  
  
|||  
|-|-|  
|Détails|Dans certains scénarios multithreads, `ConcurentQueue<T>.TryPeek` peut retourner la valeur true, mais renseigner le paramètre de sortie avec la valeur Null (au lieu de la valeur correcte).|  
|Suggestion|Ce problème a été résolu dans le .NET Framework 4.5.1. Pour résoudre votre problème, effectuez une mise niveau vers le .NET Framework 4.5.1.|  
|Portée|Majeur|  
|Version|4.5-4.5.1|  
|Type|Exécution|  
|API affectées|<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek%28%600%40%29?displayProperty=fullName>|  
|Analyseurs|CD0095|  
  
<a name="diagnostic98"></a>   
## <a name="98-multiple-items-in-a-single-tablelayoutpanel-cell-may-be-rearranged"></a>98 : Plusieurs éléments contenus dans une même cellule TableLayoutPanel peuvent être réorganisés  
  
|||  
|-|-|  
|Détails|Dans le .NET Framework 4.5, si plusieurs éléments sont placés dans la même cellule TableLayoutPanel, ils peuvent s’afficher dans un autre ordre que celui dans lequel ils s’affichent dans le .NET Framework 4.0.|  
|Suggestion|L’ancien comportement a été restauré dans une mise à jour de maintenance pour le .NET Framework 4.5. Pour résoudre ce problème, mettez à jour .NET Framework 4.5 ou mettez-le à niveau vers .NET Framework 4.5.1 ou version ultérieure. Vous pouvez également éviter de placer plusieurs éléments dans une même cellule TableLayourPanel.|  
|Portée|Mineur|  
|Version|4.5-4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Windows.Forms.TableLayoutControlCollection.Add%28System.Windows.Forms.Control%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>|  
|Analyseurs|CD0098|  
  
<a name="diagnostic100"></a>   
## <a name="100-foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>100 : La variable d’itérateur foreach est désormais délimitée au sein de l’itération. La sémantique de capture de clôture est donc différente (en C# 5)  
  
|||  
|-|-|  
|Détails|À compter de la version 5 du langage C# (Visual Studio 2012), les variables d’itérateur foreach sont délimitées au sein de l’itération. Cela peut provoquer des arrêts d’exécution si le code dépendait du fait que les variables ne soient pas incluses dans la clôture de foreach. Les conséquences de ce changement sont qu’une variable d’itérateur passée à un délégué sera considérée comme la valeur qu’elle avait au moment où le délégué a été créé, plutôt que comme la valeur qu’elle avait au moment où le délégué a été appelé.|  
|Suggestion|Dans l’idéal, le code doit être mis à jour pour prévoir ce nouveau comportement du compilateur. Si vous avez besoin de l’ancienne sémantique, la variable d’itérateur peut être remplacée par une autre variable placée explicitement en dehors de la portée de la boucle.|  
|Portée|Majeur|  
|Version|4.5|  
|Type|Reciblage|  
|Analyseurs|CD0100|  
  
<a name="diagnostic101"></a>   
## <a name="101-htmltextwriter-does-not-render-br-element-correctly"></a>101 : HtmlTextWriter n’effectue pas correctement le rendu de l’élément \`<br/\>`  
  
|||  
|-|-|  
|Détails|À compter de la version 4.6 du .NET Framework, l’appel de `HtmlTextWriter.RenderBeginTag()` et `HtmlTextWriter.RenderEndTag()` avec un élément `<BR />` aboutit à l’insertion d’un seul `<BR />` (au lieu de deux).|  
|Suggestion|Si une application dépendait de la balise `<BR />` supplémentaire, `HtmlTextWriter.RenderBeginTag()` doit être appelé une deuxième fois. Notez que ce comportement affecte uniquement les applications qui ciblent le .NET Framework 4.6. Vous pouvez également cibler une version antérieure du .NET Framework pour obtenir l’ancien comportement.|  
|Portée|Limité|  
|Version|4.6|  
|Type|Reciblage|  
|API affectées|<xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName>|  
|Analyseurs|CD0101|  
  
<a name="diagnostic104"></a>   
## <a name="104-calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>104 : L’appel d’Items.Refresh dans un contrôle WPF ListBox, ListView ou DataGrid contenant des éléments sélectionnés peut provoquer des doublons  
  
|||  
|-|-|  
|Détails|Dans le .NET Framework 4.5, si vous appelez ListBox.Items.Refresh à partir du code alors que des éléments sont sélectionnés dans un ListBox, les éléments en question peuvent apparaître deux fois dans la liste. Un problème similaire se produit avec ListView et DataGrid. Ce problème a été résolu dans le .NET Framework 4.6.|  
|Suggestion|Ce problème peut être contourné en désélectionnant les éléments par programmation avant que Refresh ne soit appelé, puis en sélectionnant de nouveau les éléments une fois l’appel terminé. Étant donné que ce problème a été résolu dans le .NET Framework 4.6, vous pouvez également mettre à niveau votre version du .NET Framework.|  
|Portée|Mineur|  
|Version|4.5-4.6|  
|Type|Exécution|  
|API affectées|<xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName>|  
|Analyseurs|CD0104|  
  
<a name="diagnostic105"></a>   
## <a name="105-etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>105 : Les EventListeners ETW ne capturent pas les événements provenant de fournisseurs avec des mots clés explicites (comme le fournisseur TPL)  
  
|||  
|-|-|  
|Détails|Les EventListeners ETW avec un masque de mot clé vide ne capturent pas correctement les événements provenant de fournisseurs ayant des mots clés explicites. Dans le .NET Framework 4.5, le fournisseur TPL fournissait des mots clés explicites et provoquait ce problème. Dans le .NET Framework 4.6, les EventListeners ont été mis à jour pour ne plus causer ce problème.|  
|Suggestion|Pour contourner ce problème, remplacez les appels à EnableEvents (eventSource, level) par des appels à la surcharge EnableEvents qui spécifie explicitement le masque « tous les mots clés » à utiliser : `EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))`.<br /><br /> Étant donné que ce problème a été résolu dans le .NET Framework 4.6, vous pouvez également mettre à niveau votre version du .NET Framework.|  
|Portée|Limité|  
|Version|4.5-4.6|  
|Type|Exécution|  
|API affectées|<xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%29?displayProperty=fullName>|  
|Analyseurs|CD0105|  
  
<a name="diagnostic109"></a>   
## <a name="109-building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>109 : La génération d’un fichier edmx Entity Framework avec Visual Studio 2013 peut échouer avec l’erreur MSB4062 si vous utilisez les tâches EntityDeploySplit ou EntityClean  
  
|||  
|-|-|  
|Détails|L’emplacement des fichiers des outils MSBuild 12.0 (inclus dans Visual Studio 2013) a changé, ce qui rend les anciens fichiers de cibles Entity Framework non valides. Les tâches `EntityDeploySplit` et `EntityClean` échouent, car elles ne parviennent pas à trouver `Microsoft.Data.Entity.Build.Tasks.dll`. Ce problème est dû à une modification d’un ensemble d’outils (msbuild/VS), et non à une modification du .NET Framework. Il est dû à la mise à niveau des outils de développement, et non à celle du .NET Framework.|  
|Suggestion|Les fichiers de cibles Entity Framework ont été corrigés pour fonctionner avec la nouvelle disposition msbuild du .NET Framework 4.6. Vous pouvez résoudre ce problème en mettant à niveau votre .NET Framework vers la version 4.6. Vous pouvez également utiliser [cette solution de contournement](http://stackoverflow.com/a/24249247/131944) pour corriger directement les fichiers cibles.|  
|Portée|Majeur|  
|Version|4.5.1-4.6|  
|Type|Reciblage|  
|Analyseurs|CD0109|  
  
<a name="diagnostic111"></a>   
## <a name="111-xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>111 : La validation de schéma XSD détecte désormais les violations de contraintes uniques si des clés composées sont utilisées et que l’une d’elles est vide  
  
|||  
|-|-|  
|Détails|Les versions du .NET Framework antérieures à 4.6 contenaient un bogue qui empêchait la validation XSD de détecter les contraintes uniques des clés composées si l’une d’elles était vide. Dans le .NET Framework 4.6, ce problème est résolu. La validation est désormais plus précise. Toutefois, il se peut que du code XML ne soit plus validé, alors qu’il l’était dans les versions précédentes.|  
|Suggestion|Si la validation moins précise du .NET Framework 4.0 est nécessaire, l’application de validation peut cibler la version 4.5 (ou version antérieure) du .NET Framework. Toutefois, lorsque vous reciblez vers .NET 4.6, passez en revue le code pour vérifier que les clés composées en double (comme décrit plus haut) ne sont pas censées être validées.|  
|Portée|Limité|  
|Version|4.6|  
|Type|Reciblage|  
|Analyseurs|CD0111|  
  
<a name="diagnostic112"></a>   
## <a name="112-calling-attributegetcustomattributes-on-an-indexer-property-no-longer-throws-ambiguousmatchexception-if-the-ambiguity-can-be-resolved-by-indexs-type"></a>112 : L’appel d’Attribute.GetCustomAttributes sur une propriété d’indexeur ne lève plus d’exception AmbiguousMatchException si l’ambiguïté peut être résolue par type d’index  
  
|||  
|-|-|  
|Détails|Avant le .NET Framework 4.6, l’appel de `GetCustomAttribute(s)` sur une propriété d’indexeur qui différait d’une autre propriété uniquement par son type d’index entraînait une `AmbiguousMatchException`. À compter de la version 4.6 du .NET Framework, les attributs de la propriété sont correctement retournés.|  
|Suggestion|Notez que GetCustomAttribute(s) fonctionne plus fréquemment à présent. Si une application comptait sur l’exception `AmbiguousMatchException`, utilisez la réflexion pour rechercher explicitement plusieurs indexeurs.|  
|Portée|Limité|  
|Version|4.6|  
|Type|Exécution|  
|API affectées|<xref:System.Attribute.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName>|  
|Analyseurs|CD0112|  
  
<a name="diagnostic113"></a>   
## <a name="113-intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>113 : Impossibilité par intermittence de faire défiler un élément jusqu’en bas dans les ItemsControls (tels que ListBox et DataGrid) lors de l’utilisation de DataTemplates personnalisés  
  
|||  
|-|-|  
|Détails|Dans certains cas, un bogue du .NET Framework 4.5 empêche le défilement des ItemsControls (ListBox, ComboBox, DataGrid, etc.) jusqu’au dernier élément lorsque vous utilisez des DataTemplates personnalisés. Si le défilement est tenté une deuxième fois (après avoir fait défiler jusqu’en haut), il fonctionnera.|  
|Suggestion|Étant donné que ce problème a été résolu dans le .NET Framework 4.5.2, vous pouvez également mettre à niveau votre version du .NET Framework. Vous pouvez également faire glisser les barres de défilement jusqu’au dernier élément de la collection, mais aurez peut-être à recommencer l’opération une deuxième fois pour y arriver.|  
|Portée|Mineur|  
|Version|4.5-4.5.2|  
|Type|Exécution|  
|Analyseurs|CD0113|  
  
<a name="diagnostic114"></a>   
## <a name="114-glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-45"></a>114 : GlyphRun.ComputeInkBoundingBox() et FormattedText.Extent retournent des valeurs différentes à compter de la version 4.5 du .NET  
  
|||  
|-|-|  
|Détails|Des améliorations ont été apportées à GlyphRun.ComputeInkBoundingBox() et FormattedText.Extent dans le .NET Framework 4.5 pour résoudre les problèmes liés à la taille insuffisante des rectangles pour les glyphes qu’ils contenaient dans le .NET Framework 4.0. Dans le .NET Framework 4.5, certains rectangles englobants sont désormais plus grands, ce qui entraîne des différences subtiles dans la disposition de l’interface utilisateur.|  
|Suggestion|Notez que la taille de certains rectangles englobants de glyphes a été augmentée. Ces modifications sont censées améliorer la présentation et les tests hitbox. Toutefois, si vous souhaitez utiliser l’ancien comportement (versions antérieures au .NET 4.5), ajoutez l’entrée suivante au fichier app.config :<br /><br /> `<appsettings> <add key="IncludeAllInkInBoundingBox" value="false"> </appsettings>`|  
|Portée|Limité|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=fullName><br /><br /> <xref:System.Windows.Media.FormattedText.Extent?displayProperty=fullName>|  
|Analyseurs|CD0114|  
  
<a name="diagnostic124"></a>   
## <a name="124-calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>124 : L’appel de DataGrid.CommitEdit à partir d’un gestionnaire CellEditEnding supprime le focus  
  
|||  
|-|-|  
|Détails|L’appel de DataGrid.CommitEdit à partir de l’un des gestionnaires d’événements CellEditEnding de DataGrid fait perdre le focus à DataGrid.|  
|Suggestion|Ce bogue a été résolu dans le .NET Framework 4.5.2. Vous pouvez donc l’éviter en mettant à niveau votre version du .NET Framework. Vous pouvez également contourner ce problème en resélectionnant explicitement le contrôle DataGrid après avoir appelé CommitEdit.|  
|Portée|Limité|  
|Version|4.5-4.5.2|  
|Type|Exécution|  
|API affectées|<xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName><br /><br /> <xref:System.Windows.Controls.DataGrid.CommitEdit%28System.Windows.Controls.DataGridEditingUnit%2CSystem.Boolean%29?displayProperty=fullName>|  
|Analyseurs|CD0124|  
  
<a name="diagnostic125"></a>   
## <a name="125-aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>125 : ASP.NET MVC échappe désormais les espaces dans les chaînes passées via des paramètres d’itinéraire  
  
|||  
|-|-|  
|Détails|Pour des raisons de conformité à la norme RFC 2396, les espaces situés dans les itinéraires de routage sont désormais échappés lors du remplissage des paramètres d’action à partir d’un itinéraire. Dans les versions précédentes, `/controller/action/some data` correspondait à l’itinéraire `/controller/action/{data}` et fournissait `some data` comme paramètre de données. Désormais, il fournit `some%20data` à la place.|  
|Suggestion|Le code doit être mis à jour pour ne plus échapper les paramètres de chaîne à partir d’un itinéraire. Si l’URI d’origine est nécessaire, vous pouvez y accéder avec l’API Request.RequestUri.OriginalString.|  
|Portée|Mineur|  
|Version|4.5.2|  
|Type|Exécution|  
|API affectées|[System.Web.Http.RouteAttribute](https://msdn.microsoft.com/library/system.web.http.routeattribute(v=vs.118).aspx)|  
|Analyseurs|CD0125|  
  
<a name="diagnostic127"></a>   
## <a name="127-vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>127 : VB.NET ne prend plus en charge la qualification partielle des espaces de noms pour les API System.Windows  
  
|||  
|-|-|  
|Détails|À compter de la version 4.5.2 du .NET, les projets VB.NET ne peuvent plus spécifier d’API System.Windows avec des espaces de noms partiellement qualifiés. Par exemple, la référence à `Windows.Forms.DialogResult` échoue. Le code doit référencer le nom qualifié complet (`System.Windows.Forms.DialogResult`) ou importer l’espace de noms et référencer `DialogResult`.|  
|Suggestion|Le code doit être mis à jour pour référencer les API `System.Windows` avec des noms simples (en important l’espace de noms nécessaire) ou avec des noms qualifiés complets.|  
|Portée|Mineur|  
|Version|4.5.2|  
|Type|Reciblage|  
|Analyseurs|CD0127|  
  
<a name="diagnostic129"></a>   
## <a name="129-two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>129 : La liaison de données bidirectionnelle avec une propriété ayant un accesseur Set non public n’est pas prise en charge  
  
|||  
|-|-|  
|Détails|La liaison de données avec une propriété sans accesseur Set public n’a jamais été prise en charge. À compter de la version 4.5.1 du .NET Framework, ce scénario lève une exception InvalidOperationException. Notez que cette nouvelle exception sera levée uniquement pour les applications qui ciblent spécifiquement le .NET Framework 4.5.1. Si une application cible le .NET Framework 4.5, l’appel sera autorisé. Si l’application ne cible pas une version particulière du .NET Framework, la liaison sera traitée comme étant unidirectionnelle.|  
|Suggestion|L’application doit être mise à jour pour utiliser une liaison unidirectionnelle ou exposer publiquement l’accesseur Set de la propriété. Vous pouvez également cibler le .NET Framework 4.5 pour obtenir l’ancien comportement de l’application.|  
|Portée|Mineur|  
|Version|4.5.1|  
|Type|Reciblage|  
|API affectées|<xref:System.Windows.Data.BindingMode?displayProperty=fullName>|  
|Analyseurs|CD0129|  
  
<a name="diagnostic130"></a>   
## <a name="130-marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>130 : Les surcharges Marshal.SizeOf et Marshal.PtrToStructure provoquent l’arrêt du code dynamique  
  
|||  
|-|-|  
|Détails|À compter de la version 4.5.1 du .NET Framework, la liaison dynamique des méthodes `Marshal.SizeOf` ou `Marshal.PtrToStructure` (via Windows PowerShell, IronPython ou le mot clé « dynamic » du langage C#, par exemple) peut entraîner des exceptions `MethodInvocationExceptions`, car de nouvelles surcharges de ces méthodes ont été ajoutées et peuvent être ambiguës pour les moteurs de script.|  
|Suggestion|Mettez à jour les scripts pour indiquer clairement quelle surcharge doit être utilisée. Pour cela, castez explicitement les paramètres de type de la méthode en tant que `System.Type`. Cliquez sur [ce lien](https://support.microsoft.com/kb/2909958/) pour plus de détails et d’exemples sur la manière de contourner ce problème.|  
|Portée|Mineur|  
|Version|4.5.1|  
|Type|Exécution|  
|Analyseurs|CD0130|  
  
<a name="diagnostic131"></a>   
## <a name="131-previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>131 : PreviewLostKeyboardFocus est appelé plusieurs fois si son gestionnaire affiche une boîte de message Windows Forms  
  
|||  
|-|-|  
|Détails|À compter de la version 4.5 du .NET Framework, quand vous appelez `System.Windows.Forms.MessageBox.Show` à partir d’un gestionnaire `UIElement.PreviewLostKeyboardFocus`, le gestionnaire est redéclenché quand la boîte de message est fermée, ce qui peut aboutir à une boucle infinie de boîtes de message.|  
|Suggestion|Il existe deux options pour contourner ce problème :<br /><br /> Vous pouvez appeler `System.Windows.MessageBox.Show` au lieu de `System.Windows.Forms.MessageBox.Show`.<br /><br /> Vous pouvez afficher la boîte de message à partir d’un gestionnaire d’événements `LostKeyboardFocus` (au lieu du gestionnaire d’événements `PreviewLostKeyboardFocus`).|  
|Portée|Limité|  
|Version|4.5|  
|Type|Exécution|  
|API affectées|<xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=fullName>|  
|Analyseurs|CD0131|  
  
<a name="diagnostic133"></a>   
## <a name="133-a-concurrentdictionary-serialized-in-net-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-451-or-452"></a>133 : Un ConcurrentDictionary sérialisé dans le .NET 4.5 avec NetDataContractSerializer ne peut pas être désérialisé par .NET 4.5.1 ou 4.5.2  
  
|||  
|-|-|  
|Détails|En raison des modifications internes apportées au type, les objets `System.Collections.Concurrent.ConcurrentDictionary` qui sont sérialisés avec le .NET Framework 4.5 à l’aide de `NetDataContractSerializer` ne peuvent pas être désérialisés dans le .NET Framework 4.5.1 ou le .NET Framework 4.5.2.<br /><br /> Notez toutefois que l’inverse fonctionne (c’est-à-dire sérialiser avec le .NET Framework 4.5.x et désérialiser avec le .NET Framework 4.5). De même, toutes les sérialisations interversions 4.x fonctionnent avec le .NET Framework 4.6.<br /><br /> La sérialisation et la désérialisation à l’aide d’une même version du .NET Framework ne sont pas affectées.|  
|Suggestion|Si vous devez sérialiser et désérialiser un ConcurrentDictionary entre le .NET Framework 4.5 et le .NET Framework 4.5.1/4.5.2, utilisez un autre sérialiseur tel que DataContractSerializer ou BinaryFormatter, au lieu de NetDataContractSerializer.<br /><br /> Étant donné que ce problème a été résolu dans le .NET Framework 4.6, vous pouvez également mettre à niveau votre version du .NET Framework.|  
|Portée|Mineur|  
|Version|4.5.1-4.6|  
|Type|Exécution|  
|Analyseurs|CD0133|  
  
<a name="diagnostic134"></a>   
## <a name="134-persian-calendar-now-uses-the-hijri-solar-algorithm"></a>134 : Le calendrier persan utilise désormais l’algorithme solaire hégirien  
  
|||  
|-|-|  
|Détails|À compter de la version 4.6 du .NET Framework, la classe PersianCalendar utilise l’algorithme solaire hégirien. La conversion de dates entre le calendrier persan et les autres calendriers peut produire un résultat légèrement différent à compter de la version 4.6 du .NET Framework pour les dates antérieures à 1800 ou postérieures à 2023 (calendrier grégorien).<br /><br /> En outre, `PersianCalendar.MinSupportedDateTime` est désormais `March 22, 0622 instead of March 21, 0622`.|  
|Suggestion|Notez que certaines dates anciennes ou futures peuvent être légèrement différentes lorsque vous utilisez le calendrier persan dans le .NET Framework 4.6. En outre, quand vous sérialisez des dates dans plusieurs processus qui peuvent s’exécuter sur des versions différentes du .NET Framework, ne les stockez pas sous forme de chaînes de date PersianCalendar (puisque ces valeurs peuvent être différentes).|  
|Portée|Mineur|  
|Version|4.6|  
|Type|Exécution|  
|API affectées|<xref:System.Globalization.PersianCalendar?displayProperty=fullName>|  
|Analyseurs|CD0134|  
  
<a name="diagnostic138"></a>   
## <a name="138-calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>138 : L’appel de CreateDefaultAuthorizationContext avec un argument Null a été modifié  
  
|||  
|-|-|  
|Détails|L’implémentation de l’AuthorizationContext retourné par un appel à `CreateDefaultAuthorizationContext(IList<IAuthorizationPolicy>)` avec un argument authorizationPolicies Null est désormais différente dans le .NET Framework 4.6.|  
|Suggestion|Dans de rares cas, les applications WCF qui utilisent l'authentification personnalisée peuvent voir les différences de comportement. Dans ce cas, vous pouvez restaurer l’ancien comportement de deux manières :<br /><br /> Recompiler l'application pour cibler une version antérieure du .NET Framework autre que 4.6. Pour les services hébergés dans IIS, utilisez l’élément \<httpRuntime targetFramework="x.x" /> pour cibler une version antérieure du .NET Framework.<br /><br /> Ajoutez la ligne suivante à la section `<appSettings>` de votre fichier app.config : `<add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />`|  
|Portée|Mineur|  
|Version|4.6|  
|Type|Reciblage|  
|API affectées|<xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29?displayProperty=fullName>|  
|Analyseurs|CD0138|  
  
<a name="diagnostic141"></a>   
## <a name="141-wpf-treeviewitem-must-be-used-within-a-treeview"></a>141 : Les éléments TreeViewItem WPF doivent être utilisés dans un contrôle TreeView  
  
|||  
|-|-|  
|Détails|À compter de la version 4.5 du .NET Framework, l’utilisation des éléments TreeViewItem en dehors des contrôles TreeView est désormais restreinte. Cette restriction est applicable dans les cas suivants :<br /><br /> L’objet visuel parent de TreeViewItem n’est pas un panneau (un TreeViewItem généré pour un contrôle TreeView aura un panneau comme parent).<br /><br /> Le TreeViewItem est un descendant d’un VirtualizingStackPanel ayant le rôle d’« hôte des éléments » pour un contrôle liste (ListBox, DataGrid, ListView, etc.). Il n’est pas nécessaire d’activer la virtualisation.<br /><br /> Le VirtualizingStackPanel permet le défilement des éléments d’une liste (`ScrollUnit="Item"`).<br /><br /> `VirtualizingStackPanel.MakeVisible(v)` est appelé pour faire défiler un élément `v` dans l’affichage. Vous pouvez faire ceci de manière explicite ou implicite de différentes façons. Le moyen le plus courant est de cliquer sur `v` pour lui donner le focus clavier.<br /><br /> La chaîne de l’objet visuel parent allant de `v` à VirtualizingStackPanel traverse le TreeViewItem.<br /><br /> Cela se produit lorsqu’un TreeViewItem est utilisé en dehors d’un contrôle TreeView, et que l’utilisateur clique sur un descendant de la TreeViewItem pour l’afficher. Si le TreeViewItem n’a pas de descendant pouvant être actif, vous ne rencontrez pas ce problème. Cela peut se produire lorsqu’un TreeViewItem constitue la racine d’un DataTemplate.  Une exception InvalidCastException est alors levée dans le cadre de WPF.|  
|Suggestion|Un correctif sera mis à disposition pour résoudre ce problème.|  
|Portée|Mineur|  
|Version|4.5|  
|Type|Exécution|  
|Analyseurs|CD0141|  
  
<a name="diagnostic143"></a>   
## <a name="143-x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>143 : X509CertificateClaimSet.FindClaims prend en compte tous les claimTypes  
  
|||  
|-|-|  
|Détails|Dans les applications qui ciblent le .NET Framework 4.6.1, si un jeu de revendications X509 est initialisé à partir d’un certificat dont le champ SAN a plusieurs entrées DNS, la méthode FindClaims tente de faire correspondre l’argument claimType avec toutes les entrées DNS.<br /><br /> Pour les applications qui ciblent des versions antérieures du .NET Framework, la méthode FindClaims tente de faire correspondre l’argument claimType uniquement avec la dernière entrée DNS.|  
|Suggestion|Cette modification affecte uniquement les applications qui ciblent le .NET Framework 4.6.1. Cette modification peut être désactivée (ou activée si vous ciblez une version antérieure à 4.6.1) avec le commutateur de compatibilité [DisableMultipleDNSEntries](https://msdn.microsoft.com/library/mt620030%28v=vs.110%29.aspx).|  
|Portée|Mineur|  
|Version|4.6.1|  
|Type|Reciblage|  
|API affectées|<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%28System.String%2CSystem.String%29?displayProperty=fullName>|  
|Analyseurs|CD0143|  
  
<a name="diagnostic144"></a>   
## <a name="144-applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>144 : Application.FilterMessage ne lève plus d’exceptions pour les implémentations réentrantes d’IMessageFilter.PreFilterMessage  
  
|||  
|-|-|  
|Détails|Dans les versions antérieures au .NET Framework 4.6.1, l’appel d’Application.FilterMessage avec un IMessageFilter.PreFilterMessage ayant appelé AddMessageFilter ou RemoveMessageFilter (tout en appelant également Application.DoEvents) provoque la levée d’une exception IndexOutOfRangeException.<br /><br /> Dans les applications qui ciblent le .NET Framework 4.6.1, cette exception n’est plus levée, et des filtres réentrants comme ceux décrits plus haut peuvent être utilisés.|  
|Suggestion|Notez qu’Application.FilterMessage ne lève plus d’exceptions pour le comportement réentrant d’IMessageFilter.PreFilterMessage décrit ci-dessus. Cette modification affecte uniquement les applications qui ciblent le .NET Framework 4.6.1.<br /><br /> Les applications qui ciblent le .NET Framework 4.6.1 peuvent ne pas adhérer à cette modification (et les applications qui ciblent des versions antérieures du .NET Framework peuvent y adhérer) à l’aide du commutateur de compatibilité [DontSupportReentrantFilterMessage](https://msdn.microsoft.com/library/mt620032%28v=vs.110%29.aspx).|  
|Portée|Limité|  
|Version|4.6.1|  
|Type|Reciblage|  
|API affectées|<xref:System.Windows.Forms.Application.FilterMessage%28System.Windows.Forms.Message%40%29?displayProperty=fullName>|  
|Analyseurs|CD0144|  
  
<a name="diagnostic145"></a>   
## <a name="145-currentculture-is-not-preserved-across-wpf-dispatcher-operations"></a>145 : CurrentCulture n’est pas conservé d’une opération de répartiteur WPF à l’autre  
  
|||  
|-|-|  
|Détails|À compter de la version 4.6 du .NET Framework, les modifications apportées à CurrentCulture ou CurrentUICulture dans un [répartiteur](https://msdn.microsoft.com/library/system.windows.threading.dispatcher%28v=vs.110%29.aspx) seront perdues à la fin de l’opération de répartiteur. De même, les modifications apportées à CurrentCulture ou CurrentUICulture en dehors d’une opération de répartiteur peuvent ne pas être répercutées lorsque que cette opération est exécutée.<br /><br /> Concrètement, cela signifie que les modifications apportées à CurrentCulture et CurrentUICulture peuvent ne pas être transmises entre les rappels de l’interface utilisateur de WPF et tout autre code de l’application WPF.<br /><br /> Cela est dû à une modification d’[ExecutionContext](https://msdn.microsoft.com/library/system.threading.executioncontext%28v=vs.110%29.aspx) qui entraîne le stockage de CurrentCulture et de CurrentUICulture dans le contexte d’exécution. Ceci s’applique uniquement aux applications qui ciblent le .NET Framework 4.6. Les opérations de répartiteur WPF stockent le contexte d’exécution utilisé pour commencer l’opération et restaurer le contexte précédent lorsque l’opération est terminée. Étant donné que CurrentCulture et CurrentUICulture font désormais partie de ce contexte, les modifications qui leur sont apportées dans une opération de répartiteur ne sont pas conservées en dehors de cette opération.|  
|Suggestion|Si vos applications sont affectées par ce changement, vous pouvez le contourner en stockant la valeur CurrentCulture ou CurrentUICulture souhaitée dans un champ, puis en vérifiant dans tous les corps d’opérations de répartiteur (y compris les gestionnaires de rappels d’événements de l’interface utilisateur) que les bons CurrentCulture et CurrentUICulture sont définis. Étant donné que la modification d’ExecutionContext sous-jacente à cette modification WPF affecte uniquement les applications qui ciblent le .NET Framework 4.6 ou une version ultérieure, vous pouvez éviter le problème en ciblant le .NET Framework 4.5.2.|  
|Portée|Mineur|  
|Version|4.6|  
|Type|Reciblage|  
|Analyseurs|CD0145|
