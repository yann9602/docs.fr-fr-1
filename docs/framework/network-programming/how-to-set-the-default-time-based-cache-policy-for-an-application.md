---
title: "Comment&#160;: d&#233;finir la strat&#233;gie de cache &#224; dur&#233;e d&#233;finie par d&#233;faut pour une application | Microsoft Docs"
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
helpviewer_keywords: 
  - "stratégies de cache à durée définie"
  - "cache (.NET Framework), stratégies à durée définie"
  - "stratégie de cache à durée définie par défaut"
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# Comment&#160;: d&#233;finir la strat&#233;gie de cache &#224; dur&#233;e d&#233;finie par d&#233;faut pour une application
La stratégie de cache basée sur l'heure par défaut permet à une application d'avoir son comportement de cache défini par les en\-têtes envoyés à la ressource mise en cache et le comportement de cache défini dans les sections 13 et 14 de la norme RFC 2616, disponible dans [http:\/\/www.ietf.org](http://www.ietf.org/).  Il s'agit du comportement approprié de cache pour la plupart des applications.  
  
### Pour définir la stratégie automatique par défaut d'une application  
  
1.  Créez un objet basée sur l'heure de la stratégie par défaut.  
  
2.  Définissez l'objet de stratégie par défaut pour le domaine d'application.  
  
## Exemple  
 Les deux exemples produisent dans cette section des stratégies identiques.  
  
 L'exemple suivant crée une stratégie basée sur l'heure par défaut et la définit comme valeur par défaut pour le domaine d'application.  
  
```csharp  
public static void SetDefaultTimeBasedPolicy ()  
{  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy ()  
    Dim policy = New HttpRequestCachePolicy ()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
 Vous pouvez également créer la stratégie de cache basée sur l'heure par défaut à l'aide de la classe d' <xref:System.Net.Cache.RequestCachePolicy> comme indiqué dans l'exemple suivant :  
  
```csharp  
public static void SetDefaultTimeBasedPolicy2()  
{  
    RequestCachePolicy policy = new RequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy2()  
    Dim policy As New RequestCachePolicy()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
  
```  
  
## Voir aussi  
 [Gestion du cache pour les applications réseau](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [Stratégie de cache](../../../docs/framework/network-programming/cache-policy.md)   
 [Stratégies de cache basées sur l’emplacement](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [Stratégies de cache basées sur la durée](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [\<requestCaching\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)