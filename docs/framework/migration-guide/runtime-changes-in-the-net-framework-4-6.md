---
title: "Modifications du runtime dans .NET Framework&#160;4.6 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5262bcfa-6e48-416b-8972-69cb4002d386
caps.latest.revision: 34
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# Modifications du runtime dans .NET Framework&#160;4.6
Dans de rares cas, les modifications du runtime peuvent affecter les applications existantes qui ciblent les versions antérieures du .NET Framework mais qui s'exécutent sur une version ultérieure du runtime du .NET Framework. Elles incluent également des différences de comportement entre les applications qui s'exécutent sur différents environnements du runtime du .NET Framework. Il s'agit notamment des modifications dans les domaines suivants :  
  
-   [Principal](#Core)  
  
-   [Réseau](#Networking)  
  
-   [Windows Presentation Foundation \(WPF\)](#WPF)  
  
-   [Configuration et déploiement](#Setup)  
  
-   [ClickOnce](#ClickOnce)  
  
-   [Nouveau compilateur JIT 64 bits](#RyuJIT)  
  
<a name="Core"></a>   
## Principal  
  
|Fonctionnalité|Modification|Impact|Portée|  
|--------------------|------------------|------------|------------|  
|<xref:System.Globalization.PersianCalendar?displayProperty=fullName>|À compter du [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], la classe <xref:System.Globalization.PersianCalendar> utilise l'algorithme solaire hégirien.|L'algorithme solaire hégirien produit des résultats identiques à ceux du calendrier persan actuellement utilisé en Iran et Afghanistan. Il génère également des résultats identiques à l'algorithme précédent pour les dates entre 1800 et 2023 dans le calendrier grégorien. Les dates en dehors de cette plage peuvent être affectées si la classe <xref:System.Globalization.PersianCalendar> est utilisée pour effectuer des conversions de dates \(par exemple, entre des dates du calendrier grégorien et des dates du calendrier persan\) ou pour déterminer si une année donnée est une année bissextile.<br /><br /> En raison de la modification, la propriété <xref:System.Globalization.PersianCalendar.MinSupportedDateTime%2A?displayProperty=fullName>, dont la valeur initiale correspondait à la date du 21 mars 0622, a été définie sur la date du 22 mars 0622 pour les systèmes sur lesquels le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] est installé.<br /><br /> Pour plus d'informations, voir la rubrique <xref:System.Globalization.PersianCalendar>.|Secondaire|  
|<xref:System.Runtime.Versioning.TargetFrameworkAttribute>|Pour le domaine d'application par défaut, la valeur de la propriété <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> est dérivée de <xref:System.Runtime.Versioning.TargetFrameworkAttribute>, le cas échéant, sauf si elle est explicitement définie via l'affectation d'un nom à la propriété <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName>.  Dans les versions antérieures du .NET Framework, la valeur de l'attribut <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> est `null`, sauf si un certain nombre de chemins de code spéciaux sont exécutés ou si un domaine d'application \(qui n'existe pas par défaut\) est créé sans que son infrastructure cible ne soit explicitement spécifiée dans la propriété <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName>.<br /><br /> Pour les domaines d'application qui ne sont pas des domaines d'application par défaut, il n'existe aucun changement dans la façon dont la valeur de la propriété <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> est déterminée. Si aucune valeur n'est explicitement affectée à la propriété <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName>, le domaine d'application autre que celui par défaut hérite du nom de l'infrastructure cible du domaine d'application par défaut.|Pour le domaine d'application par défaut, <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> peut retourner une valeur non null quand il a précédemment retourné `null`. Il s'agit du comportement souhaitable.|Bord|  
|<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString%28System.Boolean%29?displayProperty=fullName>|Si les certificats installés sur le système ne sont pas pris en charge par le .NET Framework, le passage d'une valeur `True` pour l'argument `verbose` retourne une chaîne valide. Dans les versions antérieures du .NET Framework, toute tentative d'accès aux informations de clé publique pour les certificats non pris en charge dans certaines situations entraîne la levée d'une exception.|Cette méthode est utilisée à titre d'information uniquement. La documentation indique qu'il est possible que la sortie ne soit pas cohérente selon les versions du .NET Framework. Ce changement affecte uniquement les applications qui appellent la méthode `ToString(True)`, et dont les certificats installés ne sont pas pris en charge par le .NET Framework. En retournant une chaîne au lieu de lever une exception, ce changement rend la méthode plus robuste.|Bord|  
|Réflexion et DCOM|Les objets de réflexion ne peuvent plus être passés du code managé aux clients DCOM hors processus. Les types suivants sont affectés : <xref:System.Reflection.Assembly>, <xref:System.Reflection.MemberInfo> et ses types dérivés, ainsi que <xref:System.Reflection.FieldInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Type> et <xref:System.Reflection.TypeInfo>, <xref:System.Reflection.MethodBody>, <xref:System.Reflection.Module> et <xref:System.Reflection.ParameterInfo>.|Les appels à [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707.aspx) pour l’objet retournent `E_NOINTERFACE`.|Secondaire|  
  
<a name="Networking"></a>   
## Réseau  
  
|Fonctionnalité|Modification|Impact|Portée|  
|--------------------|------------------|------------|------------|  
|Valeurs de date et d'heure dans la classe <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName>.|Pour se conformer aux documents [RFC822](http://www.ietf.org/rfc/rfc0822.txt) et [RFC2822](http://www.ietf.org/rfc/rfc2822.txt), une valeur de date et heure comporte maintenant deux chiffres. Auparavant, un seul chiffre était utilisé pour les valeurs qui précédaient 10:00.|Ce changement affecte les scénarios d'usage suivants :<br /><br /> -   comparaison des longueurs ou des codes de hachage des objets <xref:System.Net.Mime.ContentDisposition> sérialisés selon les versions du .NET Framework ;<br />-   comparaison de la valeur de retour de la méthode <xref:System.Net.Mime.ContentDisposition.ToString%2A> ou de la représentation sous forme de chaîne des valeurs de propriété de date et d'heure <xref:System.Net.Mime.ContentDisposition> selon les versions du .NET Framework.|Secondaire|  
  
<a name="WPF"></a>   
## Windows Presentation Foundation \(WPF\)  
  
|Fonctionnalité|Modification|Impact|Portée|  
|--------------------|------------------|------------|------------|  
|Rendu de fenêtre dans un scénario à plusieurs écrans|La totalité de la fenêtre est restituée sans découpage lorsqu'elle s'étend au\-delà d'un seul affichage dans un scénario à plusieurs écrans.|Consultez [Atténuation : rendu de la fenêtre WPF](../../../docs/framework/migration-guide/mitigation-wpf-window-rendering.md).|Secondaire|  
|Vérificateur d'orthographe sur les contrôles WPF avec texte activé|Lors de l'exécution sur Windows 10, le vérificateur d'orthographe peut ne pas fonctionner, car les fonctionnalités de vérification orthographique de la plateforme ne sont disponibles que pour les langues présentes dans la liste des langues d'entrée.|Dans Windows, 10, lorsqu'une langue est ajoutée à la liste des claviers disponibles, Windows télécharge et installe automatiquement le package correspondant de fonctionnalités à la demande, qui fournit les fonctionnalités de vérification orthographique. En ajoutant la langue à la liste des langues d'entrée, le vérificateur d'orthographe est pris en charge.|Secondaire|  
  
<a name="Setup"></a>   
## Configuration et déploiement  
  
|Fonctionnalité|Modification|Impact|Portée|  
|--------------------|------------------|------------|------------|  
|Contrôle de version de produit|Le contrôle de version de produit a changé depuis les versions précédentes du .NET Framework, notamment pour le .NET Framework 4, 4.5, 4.5.1 et 4.5.2. Pour plus d'informations, consultez [Atténuation : contrôle de version de produit](../../../docs/framework/migration-guide/mitigation-product-versioning.md).|Consultez [Atténuation : contrôle de version de produit](../../../docs/framework/migration-guide/mitigation-product-versioning.md).|Medium|  
  
<a name="ClickOnce"></a>   
## ClickOnce  
  
|Fonctionnalité|Modification|Impact|Portée|  
|--------------------|------------------|------------|------------|  
|Applications publiées avec ClickOnce, et qui utilisent un certificat de signature de code SHA\-256.|Les applications ClickOnce qui ciblent [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] ou des versions antérieures, et qui sont signées avec un certificat SHA\-256 n'ont plus de dépendance de runtime pour [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou une version ultérieure.|Auparavant, la signature d’une application ClickOnce qui ciblait [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] ou des versions antérieures avec un certificat SHA\-256 nécessitait que [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] \(ou une version ultérieure\) soit présent sur le système cible. Cela générait des erreurs dans les cas où il n'était pas présent. Ce changement a supprimé cette dépendance et permet aux certificats SHA\-256 d'être utilisés pour signer des applications ClickOnce qui ciblent [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] et les versions antérieures.|Secondaire|  
  
<a name="RyuJIT"></a>   
## Nouveau compilateur JIT 64 bits  
  
|Fonctionnalité|Modification|Impact|Portée|  
|--------------------|------------------|------------|------------|  
|Gestion des exceptions \(retour à partir d'une région `try`\)|À la différence du compilateur juste\-à\-temps JIT64 plus ancien, le nouveau compilateur JIT 64 bits n’autorise pas une instruction [ret](http://msdn.microsoft.com/library/system.reflection.emit.opcodes.ret.aspx) de code IL dans une région `try`.|Le retour à partir d'une région `try` n'est pas autorisé par la spécification ECMA\-335. Par ailleurs, aucun compilateur managé connu ne génère ce type de code IL. Toutefois, le compilateur JIT64 exécute ce code IL, s'il est généré à l'aide de l'émission de réflexion.|Bord|