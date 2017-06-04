---
title: "Comment&#160;: personnaliser une strat&#233;gie de cache bas&#233;e sur la dur&#233;e | Microsoft Docs"
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
  - "stratégies de cache basées sur la durée"
  - "personnalisation des stratégies de cache basées sur la durée"
  - "cache (.NET Framework), stratégies à durée définie"
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# Comment&#160;: personnaliser une strat&#233;gie de cache bas&#233;e sur la dur&#233;e
En créant une stratégie de cache basée sur l'heure, vous pouvez personnaliser le comportement de mise en cache en spécifiant des valeurs pour l'âge maximal, l'actualisation minimale, la péremption maximum, ou la date de synchronisation de cache.  L'objet d' <xref:System.Net.Cache.HttpRequestCachePolicy> fournit plusieurs constructeurs qui vous permettent de spécifier des combinaisons valides de ces valeurs.  
  
### Pour créer une stratégie de cache basée sur l'heure qui utilise une date de synchronisation de cache  
  
-   Créez une stratégie de cache basée sur l'heure qui utilise une date de synchronisation de cache en passant un objet d' <xref:System.DateTime> au constructeur d' <xref:System.Net.Cache.HttpRequestCachePolicy> .  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateLastSyncPolicy(DateTime when)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(when);  
        Console.WriteLine("When: {0}", when);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateLastSyncPolicy([when] As DateTime) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy([when])  
        Console.WriteLine("When: {0}", [when])  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 La sortie est similaire à ce qui suit :  
  
```  
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### Pour créer une stratégie de cache basée sur l'heure qui est basé sur l'actualisation minimale  
  
-   Créez une stratégie de cache basée sur l'heure qui est basé sur l'actualisation minimale en spécifiant <xref:System.Net.Cache.HttpCacheAgeControl> comme valeur de paramètre d' `cacheAgeControl` et en passant un objet d' <xref:System.TimeSpan> au constructeur d' <xref:System.Net.Cache.HttpRequestCachePolicy> .  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateMinFreshPolicy(TimeSpan span)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateMinFreshPolicy(span As TimeSpan) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span)  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 Pour l'appel suivant :  
  
```  
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  
  
```  
Level:Default MinFresh:3600  
  
```  
  
### Pour créer une stratégie de cache basée sur l'heure qui est basé sur l'actualisation minimale et l'âge maximal  
  
-   Créez une stratégie de cache basée sur l'heure qui est basé sur l'actualisation minimale et l'âge maximal en spécifiant <xref:System.Net.Cache.HttpCacheAgeControl> comme valeur de paramètre d' `cacheAgeControl` et en passant deux objets d' <xref:System.TimeSpan> au constructeur d' <xref:System.Net.Cache.HttpRequestCachePolicy> , un pour spécifier l'âge maximal pour les ressources et seconde spécifie l'actualisation minimale autorisée pour un objet retourné du cache.  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateFreshAndAgePolicy(TimeSpan freshMinimum, TimeSpan ageMaximum)  
    {  
        HttpRequestCachePolicy policy =   
        new HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateFreshAndAgePolicy(freshMinimum As TimeSpan, ageMaximum As TimeSpan) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum)  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 Pour l'appel suivant :  
  
```  
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  
  
```  
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## Voir aussi  
 [Gestion du cache pour les applications réseau](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [Stratégie de cache](../../../docs/framework/network-programming/cache-policy.md)   
 [Stratégies de cache basées sur l’emplacement](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [Stratégies de cache basées sur la durée](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [\<requestCaching\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)