---
title: "Prise en charge de l’identifiant de ressource internationalis&#233;e dans System.Uri | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: b5e994c3-3535-4aff-8e1b-b69be22e9a22
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# Prise en charge de l’identifiant de ressource internationalis&#233;e dans System.Uri
La classe d' <xref:System.Uri?displayProperty=fullName> a été étendue avec la prise en charge de \(IDN\) de ressource d'identificateur international \(IRI\) et des noms de domaine int.  Ces améliorations sont disponibles dans le .NET Framework 3.5, 3,0 SP1, et 2,0 SP1.  
  
## IRI et prise en charge IDN  
 Les adresses Web sont généralement exprimées à l'aide de les Uniform Resource Identifier \(URI\) qui se composent d'un jeu de caractères très limité :  
  
-   lettres ASCII majuscules et minuscules de l'alphabet anglais ;  
  
-   chiffres de 0 à 9 ;  
  
-   un petit nombre d'autres symboles ASCII.  
  
 Les spécifications applicables aux URI sont documentées dans les normes RFC 2396 et RFC 3986 publiées par l'IETF \(Internet Engineering Task Force\).  
  
 Face au développement d'Internet, la nécessité d'identifier les ressources à l'aide de langues autres que l'anglais se fait de plus en plus souvent ressentir.  Les identificateurs répondent à ce besoin et autorisent l'utilisation de caractères non ASCII \(caractères du jeu de caractères Unicode\/ISO 10646\) en guise d'IRI \(International Resource Identifiers\).  Les spécifications concernant les IRI sont documentées dans la norme RFC 3987 publiée par l'IETF.  L'utilisation d'IRI permet d'intégrer des caractères Unicode dans une URL.  
  
 La classe existante d' <xref:System.Uri?displayProperty=fullName> a été étendue pour fournir la prise en charge IRI selon la norme RFC 3987.  Les utilisateurs actuels ne percevront aucune modification dans le comportement de .NET Framework 2.0, à moins qu'ils n'activent spécifiquement des IRI.  Cela garantit la compatibilité des applications avec les versions antérieures du .NET Framework.  
  
 Une application peut spécifier s'il faut utiliser \(IDN\) analyse de l'IDN est appliquée aux noms de domaine et si les règles d'analyse de l'identificateur IRI.  Cela se fait dans le fichier machine.config ou app.config.  
  
 L'activation de l'IDN permet de convertir toutes les étiquettes Unicode d'un nom de domaine en leurs équivalents Punycode.  Les noms Punycode contiennent uniquement des caractères ASCII et commencent toujours par le préfixe xn\-\-.  L'objectif est de prendre en charge des serveurs DNS existants sur Internet, étant donné que la plupart des serveurs DNS ne prennent en charge que des caractères ASCII \(consultez RFC 3940\).  
  
 L'activation des IRI et des IDN affecte la valeur de la propriété <xref:System.Uri.DnsSafeHost%2A?displayProperty=fullName>.  L'activation des IRI et IDN peut également modifier le comportement d' <xref:System.Uri.Equals%2A?displayProperty=fullName>, d' <xref:System.Uri.OriginalString%2A?displayProperty=fullName>, d' <xref:System.Uri.GetComponents%2A?displayProperty=fullName>, et des méthodes d' <xref:System.Uri.IsWellFormedOriginalString%2A> .  
  
 La classe <xref:System.GenericUriParser?displayProperty=fullName> a également été étendue pour autoriser la création d'un analyseur personnalisable qui prend en charge les IRI et les IDN.  Le comportement d'un objet <xref:System.GenericUriParser?displayProperty=fullName> est spécifié en passant une combinaison d'opérations de bits des valeurs disponible dans l'énumération <xref:System.GenericUriParserOptions?displayProperty=fullName> au constructeur <xref:System.GenericUriParser?displayProperty=fullName>.  Le type <xref:System.GenericUriParserOptions?displayProperty=fullName> indique que l'analyseur prend en charge les règles d'analyse spécifiées dans RFC 3987 pour les IRI \(International Resource Identifiers\).  Si IRI est réellement utilisé dépend de l'IRI est activé.  
  
 Le type <xref:System.GenericUriParserOptions?displayProperty=fullName> indique que l'analyseur prend en charge l'analyse des IDN \(Internationalized Domain Name\) des noms d'hôte.  Si l'IDN est réellement utilisé dépend si l'IDN est activé.  
  
 L'activation de l'analyse IRI effectuera la vérification de la normalisation et des caractères d'après les dernières règles IRI dans la norme RFC 3987.  La valeur par défaut est pour l'analyse IRI pour être désactivé pour la vérification de la normalisation et des caractères sont effectuées selon la norme RFC 2396 et la norme RFC 3986.  
  
 IRI et IDN traitement de la classe d' <xref:System.Uri?displayProperty=fullName> peuvent également être sous contrôle à l'aide de les classes de paramètres de configuration d' <xref:System.Configuration.IriParsingElement?displayProperty=fullName> et d' <xref:System.Configuration.IdnElement?displayProperty=fullName> .  Le paramètre <xref:System.Configuration.IriParsingElement?displayProperty=fullName> active ou désactive le traitement des IRI dans la classe <xref:System.Uri?displayProperty=fullName>.  Le paramètre <xref:System.Configuration.IdnElement?displayProperty=fullName> active ou désactive le traitement des IDN dans la classe <xref:System.Uri>.  Le paramètre <xref:System.Configuration.IriParsingElement?displayProperty=fullName> contrôle également indirectement les IDN.  Le traitement des IRI doit être activé pour que le traitement des IDN soit possible.  Si le traitement des IRI est désactivé, celui des IDN aura pour valeur le paramètre par défaut, auquel cas le comportement de .NET Framework 2.0 sera utilisé pour la compatibilité et les noms IDN ne seront pas utilisés.  
  
 Le paramètre de configuration pour les classes de configuration d' <xref:System.Configuration.IriParsingElement?displayProperty=fullName> et d' <xref:System.Configuration.IdnElement?displayProperty=fullName> sera lue une fois lorsque la première classe d' <xref:System.Uri?displayProperty=fullName> est construite.  Les modifications apportées ultérieurement aux paramètres de configuration sont ignorées.  
  
## Voir aussi  
 <xref:System.Configuration.IdnElement?displayProperty=fullName>   
 <xref:System.Configuration.IriParsingElement?displayProperty=fullName>   
 <xref:System.Uri?displayProperty=fullName>   
 <xref:System.Uri.DnsSafeHost%2A?displayProperty=fullName>