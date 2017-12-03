---
title: Utilisation de JSONP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1eedacf6e98d8c6cb71b1cb62b41ce3ef7fcb47
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="using-jsonp"></a><span data-ttu-id="14038-102">Utilisation de JSONP</span><span class="sxs-lookup"><span data-stu-id="14038-102">Using JSONP</span></span>

<span data-ttu-id="14038-103">JSON Padding (JSONP) est un mécanisme qui active la prise en charge de scripts entre sites dans les navigateurs Web.</span><span class="sxs-lookup"><span data-stu-id="14038-103">JSON Padding (JSONP) is a mechanism that enables cross-site scripting support in Web browsers.</span></span> <span data-ttu-id="14038-104">JSONP repose sur la capacité des navigateurs Web à charger des scripts à partir d'un site différent de celui d'où a été extrait le document chargé en cours.</span><span class="sxs-lookup"><span data-stu-id="14038-104">JSONP is designed around the ability of Web browsers to load scripts from a site different from the one the current loaded document was retrieved from.</span></span> <span data-ttu-id="14038-105">Le mécanisme fonctionne en remplissant la charge utile du format JSON par un nom de fonction de rappel défini par l'utilisateur, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="14038-105">The mechanism works by padding the JSON payload with a user-defined callback function name, as shown in the following example.</span></span>

```javascript
callback({"a" = \\"b\\"});
```

<span data-ttu-id="14038-106">Dans l'exemple précédent la charge utile JSON, `{"a" = \\"b\\"}`, est encapsulée dans un appel de fonction, `callback`.</span><span class="sxs-lookup"><span data-stu-id="14038-106">In the preceding example the JSON payload, `{"a" = \\"b\\"}`, is wrapped in a function call, `callback`.</span></span> <span data-ttu-id="14038-107">La fonction de rappel doit déjà être définie dans la page web actuelle.</span><span class="sxs-lookup"><span data-stu-id="14038-107">The callback function must already be defined in the current Web page.</span></span> <span data-ttu-id="14038-108">Le type de contenu d’une réponse JSONP est `application/javascript`.</span><span class="sxs-lookup"><span data-stu-id="14038-108">The content type of a JSONP response is `application/javascript`.</span></span>

<span data-ttu-id="14038-109">JSONP n'est pas activé automatiquement.</span><span class="sxs-lookup"><span data-stu-id="14038-109">JSONP is not automatically enabled.</span></span> <span data-ttu-id="14038-110">Pour l'activer, affectez à l'attribut `javascriptCallbackEnabled` la valeur `true` sur l'un des points de terminaison standard HTTP (<xref:System.ServiceModel.Description.WebHttpEndpoint> ou <xref:System.ServiceModel.Description.WebScriptEndpoint>), comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="14038-110">To enable it, set the `javascriptCallbackEnabled` attribute to `true` on one of the HTTP standard endpoints (<xref:System.ServiceModel.Description.WebHttpEndpoint> or <xref:System.ServiceModel.Description.WebScriptEndpoint>), as shown in the following example.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="14038-111">Le nom de la fonction de rappel peut être spécifié dans une variable de requête nommée rappel, comme indiqué dans l'URL suivante.</span><span class="sxs-lookup"><span data-stu-id="14038-111">The name of the callback function can be specified in a query variable called callback as shown in the following URL.</span></span>

`http://baseaddress/Service/RestService?callback=functionName`

<span data-ttu-id="14038-112">En cas d'appel, le service envoie une réponse similaire à celle-ci.</span><span class="sxs-lookup"><span data-stu-id="14038-112">When invoked, the service sends a response like the following.</span></span>

```javascript
functionName({"root":"Something"});
```  

<span data-ttu-id="14038-113">Vous pouvez également spécifier le nom de la fonction de rappel en appliquant l'objet <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> à la classe de service, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="14038-113">You can also specify the callback function name by applying the <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> to the service class, as shown in the following example.</span></span>

```csharp
[ServiceContract]
[JavascriptCallbackBehavior(ParameterName = "$callback")]
public class Service1
{
    [OperationContract]
    [WebGet(ResponseFormat=WebMessageFormat.Json)]
    public string GetData()
    {
    }
}
```

<span data-ttu-id="14038-114">Pour le service illustré précédemment, une demande se présente comme suit.</span><span class="sxs-lookup"><span data-stu-id="14038-114">For the service shown previously, a request looks like the following.</span></span>

`http://baseaddress/Service/RestService?$callback=anotherFunction`

<span data-ttu-id="14038-115">En cas d'appel, le service répond comme suit.</span><span class="sxs-lookup"><span data-stu-id="14038-115">When invoked, the service responds with the following.</span></span>

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a><span data-ttu-id="14038-116">Codes d'état HTTP</span><span class="sxs-lookup"><span data-stu-id="14038-116">HTTP Status Codes</span></span>

<span data-ttu-id="14038-117">Les réponses JSONP avec des codes d'état HTTP différents de 200 incluent un deuxième paramètre avec la représentation numérique du code d'état HTTP, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="14038-117">JSONP responses with HTTP status codes other than 200 include a second parameter with the numeric representation of the HTTP status code, as shown in the following example.</span></span>

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a><span data-ttu-id="14038-118">Validations</span><span class="sxs-lookup"><span data-stu-id="14038-118">Validations</span></span>

<span data-ttu-id="14038-119">Les validations suivantes sont effectuées lorsque JSONP est activé :</span><span class="sxs-lookup"><span data-stu-id="14038-119">The following validations are performed when JSONP is enabled:</span></span>

- <span data-ttu-id="14038-120">L'infrastructure WCF lève une exception si `javascriptCallback` est activé, un paramètre de chaîne de requête de rappel est présent dans la demande et le format de réponse est défini sur JSON.</span><span class="sxs-lookup"><span data-stu-id="14038-120">The WCF infrastructure throws an exception if `javascriptCallback` is enabled, a callback query-string parameter is present in the request and the response format is set to JSON.</span></span>

- <span data-ttu-id="14038-121">Si la demande contient le paramètre de chaîne de requête de rappel mais que l'opération n'est pas HTTP GET, le paramètre de rappel est ignoré.</span><span class="sxs-lookup"><span data-stu-id="14038-121">If the request contains the callback query string parameter but the operation is not an HTTP GET, the callback parameter is ignored.</span></span>

- <span data-ttu-id="14038-122">Si le nom de rappel est `null` ou une chaîne vide, la réponse n'est pas mise au format JSONP.</span><span class="sxs-lookup"><span data-stu-id="14038-122">If the callback name is `null` or empty string the response is not formatted as JSONP.</span></span>

## <a name="see-also"></a><span data-ttu-id="14038-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14038-123">See also</span></span>

[<span data-ttu-id="14038-124">Vue d’ensemble du modèle de programmation Web HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="14038-124">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
