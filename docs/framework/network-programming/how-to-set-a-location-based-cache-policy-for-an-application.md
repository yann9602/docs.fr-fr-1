---
title: "Comment&#160;: d&#233;finir une strat&#233;gie de cache bas&#233;e sur l’emplacement pour une application | Microsoft Docs"
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
  - "définition explicite du comportement du cache"
  - "stratégies de cache basées sur l’emplacement"
  - "cache local"
  - "stratégies de cache de demande"
  - "cache (.NET Framework), stratégies basées sur l’emplacement"
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# Comment&#160;: d&#233;finir une strat&#233;gie de cache bas&#233;e sur l’emplacement pour une application
Les stratégies de cache géolocalisées permettent à une application de définir explicitement le comportement de mise en cache selon l'emplacement de la ressource demandée.  Cette rubrique montre comment définir la stratégie de cache par programme.  Pour plus d'informations sur la définition de la stratégie pour une application à l'aide de les fichiers de configuration, consultez [\<requestCaching\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
### Pour définir une stratégie de cache géolocalisée pour une application  
  
1.  Créez un objet d' <xref:System.Net.Cache.RequestCachePolicy> ou d' <xref:System.Net.Cache.HttpRequestCachePolicy> .  
  
2.  Définissez l'objet de stratégie par défaut pour le domaine d'application.  
  
### Pour définir une stratégie qui prend les ressources demandées d'un cache  
  
-   Créez une stratégie qui prend les ressources demandées d'un cache si disponible, et sinon, envoie des demandes au serveur, en définissant le cache au niveau à <xref:System.Net.Cache.HttpRequestCacheLevel>.  Une requête peut être accomplie par tout cache entre le client et serveur, notamment les caches distants.  
  
    ```csharp  
    public static void UseCacheIfAvailable()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
            (HttpRequestCacheLevel.CacheIfAvailable);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
  
    ```  
  
    ```vb  
    Public Shared Sub UseCacheIfAvailable()  
        Dim policy As New HttpRequestCachePolicy _  
             (HttpRequestCacheLevel.CacheIfAvailable)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### Pour définir une stratégie qui empêché tout cache de fournir des ressources  
  
-   Créez une stratégie qui empêché tout cache de fournir les ressources demandées en définissant le cache au niveau à <xref:System.Net.Cache.HttpRequestCacheLevel>.  Ce niveau de stratégie supprime la ressource du cache local s'il est présent et l'indique à les caches distants qu'elles doivent également supprimer la ressource.  
  
    ```csharp  
    public static void DoNotUseCache()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.NoCacheNoStore);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.NoCacheNoStore)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### Pour définir une stratégie qui retourne a demandé des ressources uniquement si elles sont dans le cache local  
  
-   Créez une stratégie qui retourne les ressources demandées uniquement si elles sont dans le cache local en définissant le cache au niveau à <xref:System.Net.Cache.HttpRequestCacheLevel>.  Si la ressource demandée n'est pas dans le cache, une exception d' <xref:System.Net.WebException> est levée.  
  
    ```csharp  
    public static void OnlyUseCache()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.CacheOnly);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub OnlyUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.CacheOnly)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### Pour définir une stratégie qui empêché le cache local de fournir des ressources  
  
-   Créez une stratégie qui empêché le cache local de fournir les ressources demandées en définissant le cache au niveau à <xref:System.Net.Cache.HttpRequestCacheLevel>.  Si la ressource demandée se trouve dans un cache intermédiaire et est correctement revalidée, le cache MSIL peut fournir la ressource demandée.  
  
    ```csharp  
    public static void DoNotUseLocalCache()  
    {  
     HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.Refresh);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseLocalCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Refresh)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### Pour définir une stratégie qui empêché tout cache de fournir les ressources demandées  
  
-   Créez une stratégie qui empêché tout cache de fournir les ressources demandées en définissant le cache au niveau à <xref:System.Net.Cache.HttpRequestCacheLevel>.  La ressource retournée par le serveur peut être stockée dans le cache.  
  
    ```csharp  
    public static void SendToServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.Reload);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub SendToServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Reload)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### Pour définir une stratégie qui autorise tout cache d'approvisionnement a demandé des ressources si la ressource sur le serveur n'est pas plus récente que la copie mise en cache  
  
-   Créez une stratégie qui autorise tout cache les ressources demandées par approvisionnement si la ressource sur le serveur n'est pas plus récente que la copie mise en cache en définissant le cache au niveau à <xref:System.Net.Cache.HttpRequestCacheLevel>.  
  
    ```csharp  
    public static void CheckServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
             (HttpRequestCacheLevel.Revalidate);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub CheckServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Revalidate)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
## Voir aussi  
 [Gestion du cache pour les applications réseau](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [Stratégie de cache](../../../docs/framework/network-programming/cache-policy.md)   
 [Stratégies de cache basées sur l’emplacement](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [Stratégies de cache basées sur la durée](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [\<requestCaching\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)