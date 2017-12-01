---
title: "Implémentation tentatives d’appel HTTP personnalisés avec interruption exponentielle"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Implémentation tentatives d’appel HTTP personnalisés avec interruption exponentielle"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 4449e5d7e0ca3c81aead26fac653de3ba2187a92
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-custom-http-call-retries-with-exponential-backoff"></a>Implémentation tentatives d’appel HTTP personnalisés avec interruption exponentielle

Pour créer des microservices résilient, vous devez gérer les scénarios de défaillance possibles HTTP. Pour cela, vous pouvez créer votre propre implémentation de nouvelles tentatives avec interruption exponentielle.

En plus de gérer l’indisponibilité de ressources temporelle, l’interruption exponentielle doit également prendre en compte que le fournisseur de cloud peut limiter la disponibilité des ressources afin d’éviter la surcharge de l’utilisation. Par exemple, la création de très rapidement trop de demandes de connexion peut être considéré comme un déni de Service ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) attaque par le fournisseur de cloud. Par conséquent, vous devez fournir un mécanisme permettant de mettre à l’échelle des demandes de connexion de retour lorsqu’un seuil de capacité a été trouvée.

En tant qu’une exploration initiale, vous pouvez implémenter votre propre code avec une classe utilitaire pour l’interruption exponentielle en [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), ainsi que du code comme suit (qui est également disponible sur un [référentiel GitHub ](https://gist.github.com/CESARDELATORRE/d80c6423a1aebaffaf387469f5194f5b)).

```csharp
public sealed class RetryWithExponentialBackoff
{
    private readonly int maxRetries, delayMilliseconds, maxDelayMilliseconds;

    public RetryWithExponentialBackoff(int maxRetries = 50,
        int delayMilliseconds = 200,
        int maxDelayMilliseconds = 2000)
    {
        this.maxRetries = maxRetries;
        this.delayMilliseconds = delayMilliseconds;
        this.maxDelayMilliseconds = maxDelayMilliseconds;
    }

    public async Task RunAsync(Func<Task> func)
    {
        ExponentialBackoff backoff = new ExponentialBackoff(this.maxRetries,
            this.delayMilliseconds,
            this.maxDelayMilliseconds);
        retry:
        try
        {
            await func();
        }
        catch (Exception ex) when (ex is TimeoutException ||
            ex is System.Net.Http.HttpRequestException)
        {
            Debug.WriteLine("Exception raised is: " +
                ex.GetType().ToString() +
                " –Message: " + ex.Message +
                " -- Inner Message: " +
                ex.InnerException.Message);
            await backoff.Delay();
            goto retry;
        }
    }
}

public struct ExponentialBackoff
{
    private readonly int m_maxRetries, m_delayMilliseconds, m_maxDelayMilliseconds;
    private int m_retries, m_pow;

    public ExponentialBackoff(int maxRetries, int delayMilliseconds,
        int maxDelayMilliseconds)
    {
        m_maxRetries = maxRetries;
        m_delayMilliseconds = delayMilliseconds;
        m_maxDelayMilliseconds = maxDelayMilliseconds;
        m_retries = 0;
        m_pow = 1;
    }

    public Task Delay()
    {
        if (m_retries == m_maxRetries)
        {
            throw new TimeoutException("Max retry attempts exceeded.");
        }
        ++m_retries;
        if (m_retries < 31)
        {
            m_pow = m_pow << 1; // m_pow = Pow(2, m_retries - 1)
        }
        int delay = Math.Min(m_delayMilliseconds * (m_pow - 1) / 2,
            m_maxDelayMilliseconds);
        return Task.Delay(delay);
    }
}
```

À l’aide de ce code dans un client C\# application (un autre microservice de client d’API Web, une application ASP.NET MVC ou même un C\# Xamarin application) est simple. L’exemple suivant montre comment, à l’aide de la classe de client HTTP.

```csharp
public async Task<Catalog> GetCatalogItems(int page,int take, int? brand, int? type)
{
    _apiClient = new HttpClient();
    var itemsQs = $"items?pageIndex={page}&pageSize={take}";
    var filterQs = "";
    var catalogUrl = $"{_remoteServiceBaseUrl}items{filterQs}?pageIndex={page}&pageSize={take}";
    var dataString = "";
    //
    // Using HttpClient with Retry and Exponential Backoff
    //
    var retry = new RetryWithExponentialBackoff();
    await retry.RunAsync(async () =>
    {
        // work with HttpClient call
        dataString = await _apiClient.GetStringAsync(catalogUrl);
    });
    return JsonConvert.DeserializeObject<Catalog>(dataString);
}
```

Toutefois, ce code est adapté uniquement comme une preuve de concept. La rubrique suivante explique comment utiliser des bibliothèques plus sophistiqués et éprouvées.


>[!div class="step-by-step"]
[Précédente] (implement-resilient-entity-framework-core-sql-connections.md) [suivant] (implement-http-call-retries-exponential-backoff-polly.md)
