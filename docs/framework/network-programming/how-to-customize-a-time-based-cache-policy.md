---
title: "Guide pratique pour personnaliser une stratégie de cache basée sur la durée"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
caps.latest.revision: 15
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 24319898cba225a86fcdee3a0aaedc73d4c6220c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-customize-a-time-based-cache-policy"></a>Guide pratique pour personnaliser une stratégie de cache basée sur la durée
Lors de la création d’une stratégie de cache basée sur la durée, vous pouvez personnaliser le comportement de la mise en cache en spécifiant des valeurs pour l’ancienneté maximale, l’actualisation minimale, l’obsolescence maximale ou la date de synchronisation du cache. L’objet <xref:System.Net.Cache.HttpRequestCachePolicy> fournit plusieurs constructeurs qui vous permettent de spécifier des combinaisons valides de ces valeurs.  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a>Pour créer une stratégie de cache basée sur la durée qui utilise une date de synchronisation du cache  
  
-   Créez une stratégie de cache basée sur la durée qui utilise une date de synchronisation du cache en passant un objet <xref:System.DateTime> au constructeur <xref:System.Net.Cache.HttpRequestCachePolicy>.  
  
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
  
 La sortie est similaire à ce qui suit :  
  
```  
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a>Pour créer une stratégie de cache basée sur la durée qui est basée sur l’actualisation minimale  
  
-   Créez une stratégie de cache basée sur la durée qui est basée sur l’actualisation minimale en spécifiant <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> comme valeur de paramètre `cacheAgeControl` et en passant un objet <xref:System.TimeSpan> au constructeur <xref:System.Net.Cache.HttpRequestCachePolicy>.  
  
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
  
 Pour l’appel suivant :  
  
```  
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  
  
```  
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a>Pour créer une stratégie de cache basée sur la durée qui est basée sur l’actualisation minimale et l’ancienneté maximale  
  
-   Créez une stratégie de cache basée sur la durée qui est basée sur l’actualisation minimale et l’ancienneté maximale en spécifiant <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> comme valeur de paramètre `cacheAgeControl` et en passant deux objets <xref:System.TimeSpan> au constructeur <xref:System.Net.Cache.HttpRequestCachePolicy>, un pour indiquer l’ancienneté maximale des ressources et un second pour indiquer l’actualisation minimale autorisée pour un objet retourné du cache.  
  
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
  
 Pour l’appel suivant :  
  
```  
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  
  
```  
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion du cache pour les applications réseau](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [Stratégie de cache](../../../docs/framework/network-programming/cache-policy.md)   
 [Stratégies de cache basées sur l’emplacement](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [Stratégies de cache basées sur la durée](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [\<requestCaching>, élément (paramètres réseau)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)

