---
title: "Migration de votre application du Windows Store vers .NET Native | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
caps.latest.revision: 29
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 29
---
# Migration de votre application du Windows Store vers .NET Native
[!INCLUDE[net_native](../../../includes/net-native-md.md)] fournit une compilation statique des applications dans le Windows Store ou sur l'ordinateur du développeur. Cela diffère de la compilation dynamique effectuée pour les applications du Windows Store par le compilateur juste\-à\-temps \(JIT\) ou le [générateur d'images natives \(Ngen.exe\)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) sur l'appareil. Malgré les différences, [!INCLUDE[net_native](../../../includes/net-native-md.md)] essaie d’assurer la compatibilité avec [.NET pour les applications du Windows Store](http://msdn.microsoft.com/library/windows/apps/br230302.aspx). Pour l'essentiel, les éléments qui fonctionnent sur .NET pour les applications du Windows Store fonctionnent également avec [!INCLUDE[net_native](../../../includes/net-native-md.md)].  Toutefois, dans certains cas, vous pouvez rencontrer des changements de comportement. Ce document traite de ces différences entre la version .NET standard pour les applications du Windows Store et [!INCLUDE[net_native](../../../includes/net-native-md.md)] dans les domaines suivants :  
  
-   [Différences générales au moment de l'exécution](#Runtime)  
  
-   [Différences de programmation dynamique](#Dynamic)  
  
-   [Autres différences en matière de réflexion](#Reflection)  
  
-   [API et scénarios non pris en charge](#Unsupported)  
  
-   [Différences concernant Visual Studio](#VS)  
  
<a name="Runtime"></a>   
## Différences générales au moment de l'exécution  
  
-   Les exceptions, telles que <xref:System.TypeLoadException>, qui sont levées par le compilateur JIT quand une application s'exécute sur le Common Language Runtime \(CLR\) entraînent généralement des erreurs de compilation pendant le traitement par [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
-   N'appelez pas la méthode <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=fullName> à partir du thread d'interface utilisateur d'une application. Cela peut entraîner un blocage sur [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
-   Ne vous fiez pas à l'ordre d'appel des constructeurs de classe statique. Dans [!INCLUDE[net_native](../../../includes/net-native-md.md)], l'ordre d'appel est différent de l'ordre sur le runtime standard. \(Même avec le runtime standard, évitez de vous fier à l'ordre d'exécution des constructeurs de classe statique.\)  
  
-   Des boucles infinies sans appel \(par exemple, `while(true);`\) sur n'importe quel thread peuvent entraîner l'arrêt de l'application. Il en va de même dans le cas des attentes de longues durées ou infinies.  
  
-   Certains cycles d'initialisation générique ne lèvent pas d'exceptions dans [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Par exemple, le code suivant lève une exception <xref:System.TypeLoadException> sur le CLR standard, mais pas dans [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
     [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]  
  
-   Dans certains cas, [!INCLUDE[net_native](../../../includes/net-native-md.md)] fournit des implémentations différentes des bibliothèques de classes .NET Framework. Un objet retourné par une méthode implémente toujours les membres du type retourné. Toutefois, l'implémentation de sa sauvegarde étant différente, vous ne pourrez peut\-être pas effectuer un cast vers le même ensemble de types comme vous le pourriez sur d'autres plateformes .NET Framework. Par exemple, dans certains cas, vous ne pourrez peut\-être pas effectuer un cast de l'objet d'interface <xref:System.Collections.Generic.IEnumerable%601> retourné par des méthodes telles que <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=fullName> ou <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=fullName> vers `T[]`.  
  
-   Le cache WinInet n'est pas activé par défaut sur .NET pour les applications du Windows Store, mais il l'est sur [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Cela améliore les performances, mais a des implications pour les jeux de travail. Aucune action n'est nécessaire de la part du développeur.  
  
<a name="Dynamic"></a>   
## Différences de programmation dynamique  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] effectue des liaisons statiques dans le code à partir du .NET Framework pour rendre le code app\-local afin d'optimiser les performances. Cependant, la taille des binaires doit demeurer petite, pour que l'ensemble du .NET Framework ne soit pas sollicité. Le compilateur [!INCLUDE[net_native](../../../includes/net-native-md.md)] résout cette limitation en utilisant un réducteur de dépendances qui supprime les références au code non utilisé. Toutefois, [!INCLUDE[net_native](../../../includes/net-native-md.md)] ne peut pas tenir à jour ou générer certaines informations de type et du code quand ces informations ne peuvent pas être déduites statiquement au moment de la compilation, mais qu'elles sont au contraire récupérées de façon dynamique au moment de l'exécution.  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] n'active pas la réflexion et la programmation dynamique. Toutefois, tous les types ne peuvent pas être marqués pour réflexion, car la taille du code généré serait alors trop grande \(notamment car la réflexion d'API publiques dans le .NET Framework est prise en charge\). Le compilateur [!INCLUDE[net_native](../../../includes/net-native-md.md)] choisit intelligemment les types devant prendre en charge la réflexion, et il ne conserve les métadonnées et ne génère le code que pour ces types.  
  
 Par exemple, pour la liaison de données, une application doit pouvoir mapper les noms de propriété sur les fonctions. Dans .NET pour les applications du Windows Store, le Common Language Runtime utilise automatiquement la réflexion pour fournir cette fonctionnalité pour les types managés et les types natifs disponibles publiquement. Dans [!INCLUDE[net_native](../../../includes/net-native-md.md)], le compilateur inclut automatiquement les métadonnées des types auxquels vous liez des données.  
  
 Le compilateur [!INCLUDE[net_native](../../../includes/net-native-md.md)] peut également gérer les types génériques couramment utilisés tels que <xref:System.Collections.Generic.List%601> et <xref:System.Collections.Generic.Dictionary%602>, qui fonctionnent sans indications ou directives. Le mot clé [dynamic](../Topic/dynamic%20\(C%23%20Reference\).md) est également pris en charge, dans certaines limites.  
  
> [!NOTE]
>  Vous devez tester minutieusement tous les chemins de code dynamiques quand vous portez votre application vers [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 La configuration par défaut pour [!INCLUDE[net_native](../../../includes/net-native-md.md)] est suffisante pour la plupart des développeurs, mais certains peuvent souhaiter affiner leurs configurations à l'aide d'un fichier de directives runtime \(.rd.xml\). En outre, dans certains cas, le compilateur [!INCLUDE[net_native](../../../includes/net-native-md.md)] est incapable de déterminer les métadonnées indispensables pour la réflexion et s'appuie sur les indicateurs, notamment dans les cas suivants :  
  
-   Certaines constructions telles que <xref:System.Type.MakeGenericType%2A?displayProperty=fullName> et <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=fullName> ne peuvent pas être déterminées de manière statique.  
  
-   Comme le compilateur ne peut pas déterminer les instanciations, un type générique à réfléchir doit être spécifié par les directives runtime. Cela est nécessaire à double titre : tout le code doit être inclus, et la réflexion de types génériques peut former un cycle infini \(par exemple, quand une méthode générique est appelée sur un type générique\).  
  
> [!NOTE]
>  Les directives runtime sont définies dans un fichier de directives runtime \(.rd.xml\). Pour des informations générales sur l’utilisation de ce fichier, consultez [Prise en main](../../../docs/framework/net-native/getting-started-with-net-native.md). Pour plus d’informations sur les directives runtime, consultez [Guide de référence du fichier de configuration des directives runtime \(rd.xml\)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] inclut également des outils de profilage qui permettent au développeur de déterminer quels types en dehors du jeu par défaut doivent prendre en charge la réflexion.  
  
<a name="Reflection"></a>   
## Autres différences en matière de réflexion  
 Le comportement de .NET pour les applications du Windows Store et de [!INCLUDE[net_native](../../../includes/net-native-md.md)] présente un certain nombre d'autres différences liées à la réflexion.  
  
 Dans [!INCLUDE[net_native](../../../includes/net-native-md.md)] :  
  
-   La réflexion privée de types et de membres de la bibliothèque de classes .NET Framework n'est pas prise en charge. Vous pouvez, toutefois, réfléchir vos propres types et membres privés, ainsi que les types et les membres dans des bibliothèques tierces.  
  
-   La propriété <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=fullName> retourne correctement `false` pour un objet <xref:System.Reflection.ParameterInfo> qui représente une valeur de retour. Dans .NET pour les applications du Windows Store, elle retourne `true`. Le langage intermédiaire ne prend pas cela en charge directement et l'interprétation est laissée au langage.  
  
-   Les membres publics sur les structures <xref:System.RuntimeFieldHandle> et <xref:System.RuntimeMethodHandle> ne sont pas pris en charge. Ces types sont pris en charge uniquement pour LINQ, les arborescences d'expression et l'initialisation de tableau statique.  
  
-   <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=fullName> et <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=fullName> comprennent des membres masqués dans des classes de base et peuvent donc être remplacés sans substitutions explicites. Cela vaut également pour les autres méthodes [RuntimeReflectionExtensions.GetRuntime\*](http://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx).  
  
-   <xref:System.Type.MakeArrayType%2A?displayProperty=fullName> et <xref:System.Type.MakeByRefType%2A?displayProperty=fullName> n'échouent pas quand vous essayez de créer certaines combinaisons \(par exemple, un tableau de valeurs byref\).  
  
-   Vous ne pouvez pas utiliser la réflexion pour appeler des membres qui ont des paramètres de pointeur.  
  
-   Vous ne pouvez pas utiliser la réflexion pour obtenir ou définir un champ de pointeur.  
  
-   Quand le nombre d'arguments et le type de l'un des arguments sont incorrects, [!INCLUDE[net_native](../../../includes/net-native-md.md)] lève une <xref:System.ArgumentException> au lieu d'une <xref:System.Reflection.TargetParameterCountException>.  
  
-   La sérialisation binaire des exceptions n'est généralement pas prise en charge. Ainsi, les objets non sérialisables peuvent être ajoutés au dictionnaire <xref:System.Exception.Data%2A?displayProperty=fullName>.  
  
<a name="Unsupported"></a>   
## API et scénarios non pris en charge  
 Les sections suivantes répertorient les API et les scénarios non pris en charge pour le développement général, l'interopérabilité et les technologies telles que HTTPClient et Windows Communication Foundation \(WCF\) :  
  
-   [Développement général](#General)  
  
-   [HttpClient](#HttpClient)  
  
-   [Interop](#Interop)  
  
-   [API non prises en charge](#APIs)  
  
<a name="General"></a>   
### Différences de développement général  
 **Types de valeur**  
  
-   Si vous substituez les méthodes <xref:System.ValueType.Equals%2A?displayProperty=fullName> et <xref:System.ValueType.GetHashCode%2A?displayProperty=fullName> pour un type de valeur, n'appelez pas les implémentations de classe de base. Dans .NET pour les applications du Windows Store, ces méthodes reposent sur la réflexion. Au moment de la compilation, [!INCLUDE[net_native](../../../includes/net-native-md.md)] génère une implémentation qui ne repose pas sur la réflexion de runtime. Cela signifie que si vous ne substituez pas ces deux méthodes, elles fonctionnent comme prévu, car [!INCLUDE[net_native](../../../includes/net-native-md.md)] génère l'implémentation au moment de la compilation. Toutefois, la substitution de ces méthodes tout en appelant l'implémentation de la classe de base entraîne une exception.  
  
-   Les types de valeur supérieurs à un mégaoctet ne sont pas pris en charge.  
  
-   Les types de valeur ne peuvent pas avoir de constructeur par défaut dans [!INCLUDE[net_native](../../../includes/net-native-md.md)]. \(C\# et Visual Basic interdisent les constructeurs par défaut sur les types de valeur. Toutefois, ceux\-ci peuvent être créés dans un langage intermédiaire.\)  
  
 **Tableaux**  
  
-   Les tableaux présentant une limite inférieure différente de zéro ne sont pas pris en charge. En règle générale, ces tableaux sont créés en appelant la surcharge [Array.CreateInstance\(Type, Int32\[\], Int32\<xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=fullName>.  
  
-   La création dynamique de tableaux multidimensionnels n'est pas prise en charge. Ces tableaux sont généralement créés en appelant une surcharge de la méthode <xref:System.Array.CreateInstance%2A?displayProperty=fullName> qui inclut un paramètre `lengths`, ou en appelant la méthode <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=fullName>.  
  
-   Les tableaux multidimensionnels qui ont quatre dimensions ou plus ne sont pas pris en charge ; il s'agit de tableaux dont la propriété <xref:System.Array.Rank%2A?displayProperty=fullName> à une valeur supérieure ou égale à quatre. Utilisez des [tableaux en escalier](../Topic/Jagged%20Arrays%20\(C%23%20Programming%20Guide\).md) \(tableaux de tableaux\) à la place. Par exemple, `array[x,y,z]` n'est pas valide, contrairement à `array[x][y][z]`.  
  
-   L'écart entre les tableaux multidimensionnels n'est pas pris en charge et provoque une exception <xref:System.InvalidCastException> au moment de l'exécution.  
  
 **Génériques**  
  
-   Une extension de type générique infinie entraîne une erreur du compilateur. Par exemple, la compilation de ce code échoue :  
  
     [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]  
  
 **Pointeurs**  
  
-   Les tableaux de pointeurs ne sont pas pris en charge.  
  
-   Vous ne pouvez pas utiliser la réflexion pour obtenir ou définir un champ de pointeur.  
  
 **Sérialisation**  
  
 L'attribut <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> n'est pas pris en charge. Utilisez plutôt l'attribut <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29>.  
  
 **Ressources**  
  
 L'utilisation de ressources localisées avec la classe <xref:System.Diagnostics.Tracing.EventSource> n'est pas prise en charge. La propriété <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=fullName> ne définit pas de ressources localisées.  
  
 **Délégués**  
  
 `Delegate.BeginInvoke` et `Delegate.EndInvoke` ne sont pas pris en charge.  
  
 **Async**  
  
 L'insertion de logique sous forme de thread dans les surcharges de Task IAsync n'est pas prise en charge.  
  
 **API diverses**  
  
-   La propriété <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=fullName> lève une exception <xref:System.PlatformNotSupportedException> si un attribut <xref:System.Runtime.InteropServices.GuidAttribute> n'est pas appliqué au type. Le GUID est utilisé principalement pour la prise en charge de COM.  
  
-   La méthode <xref:System.DateTime.Parse%2A?displayProperty=fullName> traite correctement les chaînes qui contiennent des dates courtes dans [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Toutefois, elle n’assure pas la compatibilité avec les changements apportés à l’analyse des dates et heures, décrits dans les articles de la Base de connaissances Microsoft [KB2803771](http://support.microsoft.com/kb/2803771) et [KB2803755](http://support.microsoft.com/kb/2803755).  
  
-   <xref:System.Numerics.BigInteger.ToString%2A?displayProperty=fullName> `("E")` est arrondi correctement dans [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Dans certaines versions du CLR, la chaîne de résultat est tronquée et non arrondie.  
  
<a name="HttpClient"></a>   
### Différences pour HttpClient  
 Dans [!INCLUDE[net_native](../../../includes/net-native-md.md)], la classe <xref:System.Net.Http.HttpClientHandler> utilise WinINet de façon interne \(via la classe [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx)\) au lieu des classes <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> utilisées dans la version .NET standard pour les applications du Windows Store.  WinINet ne prend pas en charge toutes les options de configuration prises en charge par la classe <xref:System.Net.Http.HttpClientHandler>.  Par conséquent :  
  
-   Certaines des propriétés de fonctionnalité de <xref:System.Net.Http.HttpClientHandler> retournent `false` sur [!INCLUDE[net_native](../../../includes/net-native-md.md)], tandis qu'elles retournent `true` dans la version .NET standard pour les applications du Windows Store.  
  
-   Une partie des accesseurs `get` des propriétés de configuration retournent toujours une valeur fixe sur [!INCLUDE[net_native](../../../includes/net-native-md.md)] qui est différente de la valeur configurable par défaut dans .NET pour les applications du Windows Store.  
  
 Certaines différences de comportement supplémentaires sont décrites dans les sous\-sections suivantes.  
  
 **Proxy**  
  
 La classe [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) ne prend pas en charge la configuration ou le remplacement du proxy à chaque demande.  Cela signifie que toutes les demandes présentées sur [!INCLUDE[net_native](../../../includes/net-native-md.md)] utilisent le serveur proxy configuré par le système ou aucun serveur proxy, en fonction de la valeur de la propriété <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=fullName>.  Dans .NET pour les applications du Windows Store, le serveur proxy est défini par la propriété <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=fullName>.  Sur [!INCLUDE[net_native](../../../includes/net-native-md.md)], définir <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=fullName> sur une valeur autre que `null` lève une exception <xref:System.PlatformNotSupportedException>.  La propriété <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=fullName> retourne `false` sur [!INCLUDE[net_native](../../../includes/net-native-md.md)], tandis qu'elle retourne `true` dans le .NET Framework standard pour les applications du Windows Store.  
  
 **Redirection automatique**  
  
 La classe [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) ne permet pas de configurer le nombre maximal de redirections automatiques.  La valeur de la propriété <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=fullName> est 50 par défaut dans la version .NET standard pour les applications du Windows Store et peut être modifiée. Sur [!INCLUDE[net_native](../../../includes/net-native-md.md)], la valeur de cette propriété est 10 et toute modification de cette valeur lève une exception <xref:System.PlatformNotSupportedException>.  La propriété <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=fullName> retourne `false` sur [!INCLUDE[net_native](../../../includes/net-native-md.md)], tandis qu'elle retourne `true` dans .NET pour les applications du Windows Store.  
  
 **Décompression automatique**  
  
 .NET pour les applications du Windows Store vous permet de définir la propriété <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=fullName> sur <xref:System.Net.DecompressionMethods>, <xref:System.Net.DecompressionMethods>, à la fois sur <xref:System.Net.DecompressionMethods> et <xref:System.Net.DecompressionMethods>, ou sur <xref:System.Net.DecompressionMethods>.[!INCLUDE[net_native](../../../includes/net-native-md.md)] ne prend en charge <xref:System.Net.DecompressionMethods> qu'avec <xref:System.Net.DecompressionMethods> ou <xref:System.Net.DecompressionMethods>.  Si vous essayez de définir la propriété <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> uniquement sur <xref:System.Net.DecompressionMethods> ou <xref:System.Net.DecompressionMethods>, elle est automatiquement définie à la fois sur <xref:System.Net.DecompressionMethods> et <xref:System.Net.DecompressionMethods>.  
  
 **Cookies**  
  
 La gestion des cookies est effectuée simultanément par <xref:System.Net.Http.HttpClient> et WinINet.  Les cookies de <xref:System.Net.CookieContainer> sont combinés aux cookies du cache de cookies WinINet.  La suppression d'un cookie de <xref:System.Net.CookieContainer> empêche <xref:System.Net.Http.HttpClient> de l'envoyer, mais si le cookie a déjà été vu par WinINet et que les cookies n'ont pas été supprimés par l'utilisateur, WinInet l'envoie.  Il est impossible de supprimer par programmation un cookie de WinINet à l'aide de l'API <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler> ou <xref:System.Net.CookieContainer>.  Définir la propriété <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=fullName> sur `false` entraîne uniquement l'arrêt de l'envoi des cookies par <xref:System.Net.Http.HttpClient> ; WinINet peut toujours inclure ses cookies dans la demande.  
  
 **Informations d'identification**  
  
 Dans .NET pour les applications du Windows Store, les propriétés <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=fullName> et <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=fullName> fonctionnent de manière indépendante.  En outre, la propriété <xref:System.Net.Http.HttpClientHandler.Credentials%2A> accepte tout objet qui implémente l'interface <xref:System.Net.ICredentials>.  Dans [!INCLUDE[net_native](../../../includes/net-native-md.md)], quand la propriété <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> est définie sur `true`, la propriété <xref:System.Net.Http.HttpClientHandler.Credentials%2A> prend la valeur `null`.  En outre, la propriété <xref:System.Net.Http.HttpClientHandler.Credentials%2A> peut être définie uniquement sur `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A> ou un objet de type <xref:System.Net.NetworkCredential>.  L'affectation de tout autre objet <xref:System.Net.ICredentials>, le plus courant étant <xref:System.Net.CredentialCache>, à la propriété <xref:System.Net.Http.HttpClientHandler.Credentials%2A> lève une <xref:System.PlatformNotSupportedException>.  
  
 **Autres fonctionnalités non prises en charge ou non configurables**  
  
 Dans [!INCLUDE[net_native](../../../includes/net-native-md.md)] :  
  
-   La valeur de la propriété <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=fullName> est toujours <xref:System.Net.Http.ClientCertificateOption>.  Dans .NET pour les applications du Windows Store, la valeur par défaut est <xref:System.Net.Http.ClientCertificateOption>.  
  
-   La propriété <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=fullName> n'est pas configurable.  
  
-   La propriété <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=fullName> a toujours la valeur `true`.  Dans .NET pour les applications du Windows Store, la valeur par défaut est `false`.  
  
-   L'en\-tête `SetCookie2` dans les réponses est ignoré, car considéré comme obsolète.  
  
<a name="Interop"></a>   
### Différences concernant l'interopérabilité  
 **API déconseillées**  
  
 Un certain nombre d'API peu utilisées pour l'interopérabilité avec du code managé ont été déconseillées. Quand elles sont utilisées avec [!INCLUDE[net_native](../../../includes/net-native-md.md)], ces API peuvent lever une exception <xref:System.NotImplementedException> ou <xref:System.PlatformNotSupportedException>, ou entraîner une erreur du compilateur. Dans .NET pour les applications du Windows Store, ces API sont marquées comme obsolètes, même si les appeler génère un avertissement, plutôt qu'une erreur, du compilateur.  
  
 API déconseillées pour le marshaling `VARIANT` :  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.VarEnum?displayProperty=fullName>|  
  
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> est pris en charge, mais lève une exception dans certains scénarios, par exemple quand il est utilisé avec [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) ou des variants byref.  
  
 API déconseillées pour la prise en charge de [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) :  
  
|Type|Membre|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.ClassInterfaceType>|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.ClassInterfaceType>|  
|<xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=fullName>|L'attribut n'est pas pris en charge|  
  
 API déconseillées pour les événements COM classiques :  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|  
  
 API déconseillées dans l'interface <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=fullName>, non prises en charge dans [!INCLUDE[net_native](../../../includes/net-native-md.md)] :  
  
|Type|Membre|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=fullName>|Tous les membres.|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=fullName>|Tous les membres.|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=fullName>|Tous les membres.|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>|  
  
 Autres fonctionnalités d'interopérabilité non prises en charge :  
  
|Type|Membre|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=fullName>|Tous les membres.|  
|<xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=fullName>|Tous les membres.|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.UnmanagedType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.UnmanagedType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.UnmanagedType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.UnmanagedType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.UnmanagedType>|  
  
 API de marshaling rarement utilisées :  
  
|Type|Membre|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29>|  
  
 **Appel de plateforme et compatibilité avec l'interopérabilité COM**  
  
 La plupart des scénarios d'appel de plateforme et d'interopérabilité COM sont toujours pris en charge dans [!INCLUDE[net_native](../../../includes/net-native-md.md)]. En particulier, toute l'interopérabilité avec les API Windows Runtime \(WinRT\) et tout le marshaling nécessaire pour le Windows Runtime sont pris en charge. Cela inclut la prise en charge du marshaling pour les éléments suivants :  
  
-   Tableaux \(y compris <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>\)  
  
-   `BStr`  
  
-   Délégués  
  
-   Chaînes \(Unicode, Ansi et HSTRING\)  
  
-   Structures \(`byref` et `byval`\)  
  
-   Unions  
  
-   Handles Win32  
  
-   Toutes les constructions WinRT  
  
-   Prise en charge partielle du marshaling des types variant. Les fonctionnalités suivantes sont prises en charge :  
  
    -   <xref:System.Boolean>  
  
    -   <xref:System.Byte>  
  
    -   <xref:System.Decimal>  
  
    -   <xref:System.Double>  
  
    -   <xref:System.Int16>  
  
    -   <xref:System.Int32>  
  
    -   <xref:System.Int64>  
  
    -   <xref:System.SByte>  
  
    -   <xref:System.Single>  
  
    -   <xref:System.UInt16>  
  
    -   <xref:System.UInt32>  
  
    -   <xref:System.UInt64>  
  
    -   `BStr`  
  
    -   [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509.aspx)  
  
 Toutefois, [!INCLUDE[net_native](../../../includes/net-native-md.md)] ne prend pas en charge les opérations suivantes :  
  
-   L'utilisation d'événements COM classiques  
  
-   La mise en œuvre de l'interface <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=fullName> sur un type managé  
  
-   L’implémentation de l’interface [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) sur un type managé via l’attribut <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=fullName>. Toutefois, vous ne pouvez pas appeler des objets COM via `IDispatch`, et votre objet managé ne peut pas implémenter `IDispatch`.  
  
 Utiliser la réflexion pour appeler une méthode d'appel de plateforme n'est pas pris en charge. Vous pouvez contourner cette limitation en encapsulant l'appel de méthode dans une autre méthode et en utilisant la réflexion pour appeler le wrapper.  
  
<a name="APIs"></a>   
### Autres différences par rapport aux API .NET pour les applications du Windows Store  
 Cette section répertorie les API restantes qui ne sont pas prises en charge dans [!INCLUDE[net_native](../../../includes/net-native-md.md)]. La plus grande partie des API non prises en charge sont des API Windows Communication Foundation \(WCF\).  
  
 **DataAnnotations \(System.ComponentModel.DataAnnotations\)**  
  
 Les types dans les espaces de noms <xref:System.ComponentModel.DataAnnotations> et <xref:System.ComponentModel.DataAnnotations.Schema> ne sont pas pris en charge dans [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Ceux\-ci comprennent les types suivants présents dans .NET pour les applications du Windows Store pour Windows 8 :  
  
||  
|-|  
|<xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EditableAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=fullName>|  
  
 **Visual Basic**  
  
 Visual Basic n'est pas actuellement pris en charge dans [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Les types suivants dans les espaces de noms <xref:Microsoft.VisualBasic> et <xref:Microsoft.VisualBasic.CompilerServices> ne sont pas disponibles dans [!INCLUDE[net_native](../../../includes/net-native-md.md)]:  
  
||  
|-|  
|<xref:Microsoft.VisualBasic.CallType?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.Constants?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.Strings?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=fullName>|  
  
 **Contexte de réflexion \(espace de noms System.Reflection.Context\)**  
  
 La classe <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=fullName> n'est pas prise en charge dans [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 **RTC \(System.Net.Http.Rtc\)**  
  
 La classe <xref:System.Net.Http.RtcRequestFactory?displayProperty=fullName> n'est pas prise en charge dans [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 **Windows Communication Foundation \(WCF\) \(System.ServiceModel.\*\)**  
  
 Les types dans les [espaces de noms System.ServiceModel.\*](http://msdn.microsoft.com/library/gg145010.aspx) ne sont pas pris en charge dans [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Ce sont notamment les types suivants :  
  
||  
|-|  
|<xref:System.ServiceModel.ActionNotSupportedException?displayProperty=fullName>|  
|<xref:System.ServiceModel.BasicHttpBinding?displayProperty=fullName>|  
|<xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=fullName>|  
|<xref:System.ServiceModel.BasicHttpSecurity?displayProperty=fullName>|  
|<xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=fullName>|  
|<xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.ChannelFactory?displayProperty=fullName>|  
|<xref:System.ServiceModel.ChannelFactory%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.ClientBase%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=fullName>|  
|<xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=fullName>|  
|<xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=fullName>|  
|<xref:System.ServiceModel.CommunicationException?displayProperty=fullName>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=fullName>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=fullName>|  
|<xref:System.ServiceModel.CommunicationState?displayProperty=fullName>|  
|<xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=fullName>|  
|<xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.DuplexClientBase%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.EndpointAddress?displayProperty=fullName>|  
|<xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=fullName>|  
|<xref:System.ServiceModel.EndpointIdentity?displayProperty=fullName>|  
|<xref:System.ServiceModel.EndpointNotFoundException?displayProperty=fullName>|  
|<xref:System.ServiceModel.EnvelopeVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.ExceptionDetail?displayProperty=fullName>|  
|<xref:System.ServiceModel.FaultCode?displayProperty=fullName>|  
|<xref:System.ServiceModel.FaultContractAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.FaultException?displayProperty=fullName>|  
|<xref:System.ServiceModel.FaultException%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.FaultReason?displayProperty=fullName>|  
|<xref:System.ServiceModel.FaultReasonText?displayProperty=fullName>|  
|<xref:System.ServiceModel.HttpBindingBase?displayProperty=fullName>|  
|<xref:System.ServiceModel.HttpClientCredentialType?displayProperty=fullName>|  
|<xref:System.ServiceModel.HttpTransportSecurity?displayProperty=fullName>|  
|<xref:System.ServiceModel.IClientChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.ICommunicationObject?displayProperty=fullName>|  
|<xref:System.ServiceModel.IContextChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=fullName>|  
|<xref:System.ServiceModel.IExtensibleObject%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.IExtension%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.IExtensionCollection%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.InstanceContext?displayProperty=fullName>|  
|<xref:System.ServiceModel.InvalidMessageContractException?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageContractAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageCredentialType?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageHeader%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageHeaderException?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageParameterAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageSecurityVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.NetHttpBinding?displayProperty=fullName>|  
|<xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=fullName>|  
|<xref:System.ServiceModel.NetTcpBinding?displayProperty=fullName>|  
|<xref:System.ServiceModel.NetTcpSecurity?displayProperty=fullName>|  
|<xref:System.ServiceModel.OperationContext?displayProperty=fullName>|  
|<xref:System.ServiceModel.OperationContextScope?displayProperty=fullName>|  
|<xref:System.ServiceModel.OperationContractAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.OperationFormatStyle?displayProperty=fullName>|  
|<xref:System.ServiceModel.ProtocolException?displayProperty=fullName>|  
|<xref:System.ServiceModel.QuotaExceededException?displayProperty=fullName>|  
|<xref:System.ServiceModel.SecurityMode?displayProperty=fullName>|  
|<xref:System.ServiceModel.ServerTooBusyException?displayProperty=fullName>|  
|<xref:System.ServiceModel.ServiceActivationException?displayProperty=fullName>|  
|<xref:System.ServiceModel.ServiceContractAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=fullName>|  
|<xref:System.ServiceModel.TcpClientCredentialType?displayProperty=fullName>|  
|<xref:System.ServiceModel.TcpTransportSecurity?displayProperty=fullName>|  
|<xref:System.ServiceModel.TransferMode?displayProperty=fullName>|  
|<xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=fullName>|  
|<xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=fullName>|  
|<xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.AddressHeader?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.CustomBinding?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.FaultConverter?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IInputChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IInputSession?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IOutputSession?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.ISession?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.Message?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageFault?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageHeader?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageProperties?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageState?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.RequestContext?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.ClientCredentials?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.ContractDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.FaultDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.IContractBehavior?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessageDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessageDirection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.OperationDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.SecurityVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.TrustVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=fullName>|  
  
### Différences entre les sérialiseurs  
 Les différences suivantes concernent la sérialisation et la désérialisation avec les classes <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> et <xref:System.Xml.Serialization.XmlSerializer> :  
  
-   Dans [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ne parviennent pas à sérialiser ou à désérialiser une classe dérivée qui a un membre de classe de base dont le type n'est pas un type de sérialisation racine. Par exemple, dans le code suivant, sérialiser ou désérialiser `Y` génère une erreur :  
  
     [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]  
  
     Le type `InnerType` n'est pas connu du sérialiseur, car les membres de la classe de base ne sont pas parcourus pendant la sérialisation.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ne parviennent pas à sérialiser une classe ou une structure qui implémente l'interface <xref:System.Collections.Generic.IEnumerable%601>. Par exemple, les types suivants ne parviennent pas à sérialiser ou à désérialiser :  
  
  
  
-   <xref:System.Xml.Serialization.XmlSerializer> ne sérialise pas la valeur d'objet suivante, car il ne connaît pas le type exact de l'objet à sérialiser :  
  
  
  
-   <xref:System.Xml.Serialization.XmlSerializer> ne parvient pas à sérialiser ou à désérialiser si le type de l'objet sérialisé est <xref:System.Xml.XmlQualifiedName>.  
  
-   Tous les sérialiseurs \(<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> et <xref:System.Xml.Serialization.XmlSerializer>\) ne parviennent pas à générer un code de sérialisation pour un type <xref:System.Xml.Linq.XElement?displayProperty=fullName> ou pour un type contenant <xref:System.Xml.Linq.XElement>. Ils affichent des erreurs de génération à la place.  
  
-   Les constructeurs suivants des types de sérialisation ne fonctionnent pas nécessairement comme prévu :  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=fullName>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29?displayProperty=fullName>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=fullName>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=fullName>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29?displayProperty=fullName>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=fullName>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29?displayProperty=fullName>  
  
    -   [XmlSerializer.XmlSerializer\(Type, Type\<xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=fullName>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29?displayProperty=fullName>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29?displayProperty=fullName>  
  
    -   [XmlSerializer.XmlSerializer\(Type, XmlAttributeOverrides, Type\<xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29?displayProperty=fullName>  
  
-   <xref:System.Xml.Serialization.XmlSerializer> ne parvient pas à générer le code pour un type dont les méthodes possèdent un des attributs suivants :  
  
    -   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <xref:System.Xml.Serialization.XmlSerializer> ne traite pas l'interface de sérialisation personnalisée <xref:System.Xml.Serialization.IXmlSerializable>. Si vous avez une classe qui implémente cette interface, <xref:System.Xml.Serialization.XmlSerializer> considère le type comme un ancien objet CLR simple et sérialise uniquement ses propriétés publiques.  
  
-   La sérialisation d'un objet <xref:System.Exception> simple, tel que l'objet suivant, ne fonctionne pas bien avec <xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> :  
  
  
  
<a name="VS"></a>   
## Différences concernant Visual Studio  
 **Exceptions et débogage**  
  
 Quand vous exécutez des applications compilées à l'aide de [!INCLUDE[net_native](../../../includes/net-native-md.md)] dans le débogueur, les exceptions de première chance sont activées pour les types d'exception suivants :  
  
-   <xref:System.MemberAccessException>  
  
-   <xref:System.TypeAccessException>  
  
 **Génération d'applications**  
  
 Recourez aux outils de génération x86 qui sont utilisés par défaut par Visual Studio. Nous vous déconseillons d'utiliser les outils MSBuild AMD64, qui se trouvent dans C:\\Program Files \(x86\)\\MSBuild\\12.0\\bin\\amd64, car ils peuvent créer des problèmes de génération.  
  
 **Profileurs**  
  
-   Le profileur d'UC Visual Studio et le profileur de mémoire XAML n'affichent pas Uniquement mon code correctement.  
  
-   Le profileur de mémoire XAML n'affiche pas avec précision les données du tas managé.  
  
-   Le profileur d'UC ne peut pas identifier correctement les modules, et affiche les noms de fonction avec préfixe.  
  
 **Projets de bibliothèque de tests unitaires**  
  
 L'activation de [!INCLUDE[net_native](../../../includes/net-native-md.md)] sur une bibliothèque de tests unitaires pour un projet d'application du Windows Store n'est pas prise en charge et entraîne l'échec de la génération du projet.  
  
## Voir aussi  
 [Prise en main](../../../docs/framework/net-native/getting-started-with-net-native.md)   
 [Guide de référence du fichier de configuration des directives runtime \(rd.xml\)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [Vue d’ensemble de .NET pour les applications Windows Store](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)   
 [Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)