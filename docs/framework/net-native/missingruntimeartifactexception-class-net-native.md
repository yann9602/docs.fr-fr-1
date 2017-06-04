---
title: "MissingRuntimeArtifactException, classe (.NET Native) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d5b3d13e-689f-4584-8ba6-44f5167a8590
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# MissingRuntimeArtifactException, classe (.NET Native)
**.NET pour applications Windows pour Windows 10, [!INCLUDE[net_native](../../../includes/net-native-md.md)] uniquement**  
  
 Exception levée quand les métadonnées d'un type ou d'un membre de type sont disponibles, mais que leur implémentation a été supprimée.  
  
 **Espace de noms :** System.Reflection  
  
> [!IMPORTANT]
>  La classe `MissingRuntimeArtifactException` est réservée à un usage interne par la chaîne d'outils [!INCLUDE[net_native](../../../includes/net-native-md.md)].  Elle n'est pas destinée à être utilisée dans du code tiers ni à traiter l'exception dans le code de votre application.  Au lieu de cela, éliminez l'exception en ajoutant des entrées à votre [fichier de directives runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  Pour plus d'informations, consultez la section Remarques.  
  
## Syntaxe  
 [!code-csharp[ProjectN#22](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingruntimeartifactexception_syntax1.cs#22)]  
  
 Notez que la classe `MissingRuntimeArtifactException` dérive de <xref:System.MemberAccessException>.  
  
 La classe `MissingRuntimeArtifactException` possède les membres suivants :  
  
## Constructeurs  
  
|Constructeur|Description|  
|------------------|-----------------|  
|`public MissingRuntimeArtifactException()`|Initialise une nouvelle instance de la classe `MissingRuntimeArtifactException` à l'aide d'un message système qui décrit l'erreur.<br /><br /> Ce constructeur est destiné à une utilisation interne par la chaîne d'outils [!INCLUDE[net_native](../../../includes/net-native-md.md)] uniquement.|  
|`public MissingRuntimeArtifactException(String message)`|Initialise une nouvelle instance de la classe `MissingRuntimeArtifactException` avec un message d'erreur spécifié.<br /><br /> Ce constructeur est destiné à une utilisation interne par la chaîne d'outils [!INCLUDE[net_native](../../../includes/net-native-md.md)] uniquement.|  
  
## Propriétés  
  
|Propriété|Description|  
|---------------|-----------------|  
|`public IDictionary Data { get; }`|Obtient une collection de paires clé\/valeur qui fournissent des informations supplémentaires définies par l'utilisateur sur l'exception.  \(Hérité de <xref:System.Exception?displayProperty=fullName>.\)|  
|`public string HelpLink { get; set; }`|Obtient ou définit un lien vers le fichier d'aide associé à cette exception.  \(Hérité de <xref:System.Exception?displayProperty=fullName>.\)|  
|`public int HResult { get; protected set; }`|Obtient ou définit la valeur `HRESULT`, valeur numérique codée qui est assignée à une exception spécifique.  \(Hérité de <xref:System.Exception?displayProperty=fullName>.\)|  
|`public Exception InnerException { get; }`|Obtient l'exception à l'origine de l'exception actuelle.  \(Hérité de <xref:System.Exception?displayProperty=fullName>.\)|  
|`public string Message { get; }`|Obtient un message qui décrit l'exception actuelle.  \(Hérité de <xref:System.Exception?displayProperty=fullName>.\)|  
|`public string Source { get; set; }`|Obtient ou définit le nom de l'application ou de l'objet à l'origine de l'erreur.  \(Hérité de <xref:System.Exception?displayProperty=fullName>.\)|  
|`public string StackTrace { get; }`|Obtient une représentation sous forme de chaîne des frames immédiats sur la pile des appels.  \(Hérité de <xref:System.Exception?displayProperty=fullName>.\)|  
|`public MethodBase TargetSite { get; }`|Obtient la méthode qui a levé l'exception actuelle.  \(Hérité de <xref:System.Exception?displayProperty=fullName>.\)|  
  
## Méthodes  
  
|Méthode|Description|  
|-------------|-----------------|  
|`public bool Equals(Object obj)`|Détermine si l'objet spécifié est identique à l'objet actif.  \(Hérité de <xref:System.Object>.\)|  
|`protected void Finalize()`|Autorise un objet à tenter de libérer des ressources et à exécuter d'autres opérations de nettoyage avant qu'il ne soit récupéré par une opération garbage collection.  \(Hérité de <xref:System.Object>.\)|  
|`public Exception GetBaseException()`|Retourne l'exception qui est la cause première d'une ou plusieurs exceptions ultérieures.  \(Hérité de <xref:System.Exception?displayProperty=fullName>.\)|  
|`public int GetHashCode()`|Retourne un code de hachage pour une instance `MissingRuntimeArtifactException`.  \(Hérité de <xref:System.Object>.\)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Définit un objet <xref:System.Runtime.Serialization.SerializationInfo> avec des informations relatives à l'exception.  \(Hérité de <xref:System.Exception?displayProperty=fullName>.\)|  
|`public Type GetType()`|Obtient le type au moment de l'exécution de l'instance actuelle.  \(Hérité de <xref:System.Exception?displayProperty=fullName>.\)|  
|`protected Object MemberwiseClone()`|Crée une copie superficielle de l'objet actuel.  \(Hérité de <xref:System.Object>.\)|  
|`public string ToString()`|Retourne la représentation sous forme de chaîne de l'exception actuelle.  \(Hérité de <xref:System.Exception?displayProperty=fullName>.\)|  
  
## Événements  
  
|Événement|Description|  
|---------------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Se produit quand une exception est sérialisée pour créer un objet d'état d'exception qui contient des données sérialisées concernant l'exception.  \(Hérité de <xref:System.Exception?displayProperty=fullName>.\)|  
  
## Détails de l'utilisation  
 L'exception `MissingRuntimeArtifactException` est levée en cas d'instanciation d'un type ou d'appel d'un membre de type dont l'implémentation a été supprimée malgré la présence de ses métadonnées.  
  
 Le fichier de directives runtime \(configuration XML\), \*.rd.xml, détermine si les métadonnées et le code d'implémentation servant à exécuter dynamiquement une méthode sont disponibles pour une application au moment de l'exécution.  Pour empêcher votre application de lever cette exception, vous devez modifier le fichier \*.rd.xml de manière à ce que les métadonnées nécessaires à un type ou membre de type soient présentes au moment de l'exécution.  Pour plus d'informations sur le format du fichier \*.rd.xml, consultez [Guide de référence du fichier de configuration des directives runtime \(rd.xml\)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
>  Comme cette exception indique que le code d'implémentation nécessaire à votre application n'est pas disponible au moment de l'exécution, vous ne devez pas gérer cette exception dans un bloc `try`\/`catch`.  Au lieu de cela, vous devez diagnostiquer la cause de l'exception et l'éliminer à l'aide d'un fichier de directives runtime.  En règle générale, vous éliminez cette exception en spécifiant la stratégie `Activate` ou `Dynamic` pour un élément de programme dans le fichier de directives runtime \(fichier \*.rd.xml\).  Pour obtenir l'entrée que vous pouvez ajouter à votre fichier de directives de runtime qui élimine l'exception, vous pouvez utiliser un des deux utilitaires de résolution des problèmes :  
>   
>  -   L'[utilitaire de résolution des problèmes MissingMetadataException](http://dotnet.github.io/native/troubleshooter/type.html) pour les types.  
> -   L'[utilitaire de résolution des problèmes MissingMetadataException](http://dotnet.github.io/native/troubleshooter/method.html) pour les méthodes.  
  
 La classe `MissingRuntimeArtifactException` ne contient pas de membres uniques ; tous ses membres sont hérités de sa classe de base, <xref:System.MemberAccessException>.  
  
## Voir aussi  
 [Guide de référence du fichier de configuration des directives runtime \(rd.xml\)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [Paramètres de stratégie de directive runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)