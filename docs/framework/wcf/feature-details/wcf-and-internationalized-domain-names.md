---
title: WCF et IDN (Internationalized Domain Names)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cae287ab440115b15f6c26209a3d40bee4f9703b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-and-internationalized-domain-names"></a><span data-ttu-id="2e8b7-102">WCF et IDN (Internationalized Domain Names)</span><span class="sxs-lookup"><span data-stu-id="2e8b7-102">WCF and Internationalized Domain Names</span></span>
<span data-ttu-id="2e8b7-103">La prise en charge a été ajoutée pour tenir compte des services WCF avec des noms IDN (Internationalized Domain Names).</span><span class="sxs-lookup"><span data-stu-id="2e8b7-103">Support has been added to allow for WCF services with Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="2e8b7-104">Un nom de domaine international est un nom de domaine qui contient des caractères non ASCII.</span><span class="sxs-lookup"><span data-stu-id="2e8b7-104">An internationalized domain name is a domain name that contains non-ASCII characters.</span></span> <span data-ttu-id="2e8b7-105">Cette prise en charge inclut la capacité d'héberger un service WCF avec un nom IDN et un client WCF pour parler à un service Web avec un nom IDN.</span><span class="sxs-lookup"><span data-stu-id="2e8b7-105">This support includes both the ability to host a WCF service with an IDN name and a WCF client to talk to a web service with an IDN name.</span></span>  
  
## <a name="systemuri-and-idn"></a><span data-ttu-id="2e8b7-106">System.Uri et IDN</span><span class="sxs-lookup"><span data-stu-id="2e8b7-106">System.Uri and IDN</span></span>  
 <span data-ttu-id="2e8b7-107"><xref:System.Uri> contient deux propriétés : <xref:System.Uri.Host%2A> et <xref:System.Uri.DnsSafeHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e8b7-107"><xref:System.Uri> has two properties <xref:System.Uri.Host%2A> and <xref:System.Uri.DnsSafeHost%2A>.</span></span> <span data-ttu-id="2e8b7-108">Ces propriétés contiennent des valeurs Unicode ou Punycode en fonction des paramètres de configuration pour IDN.</span><span class="sxs-lookup"><span data-stu-id="2e8b7-108">These properties contain Unicode or Punycode values depending upon the IDN configuration settings.</span></span>  
  
 <span data-ttu-id="2e8b7-109">L'IDN est activé dans le fichier de configuration d'une application à l'aide du XML suivant</span><span class="sxs-lookup"><span data-stu-id="2e8b7-109">IDN is enabled in an application’s configuration file using the following XML</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 <span data-ttu-id="2e8b7-110">Le \<idn > élément contient l’attribut activé qui peut être définie à une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="2e8b7-110">The \<idn> element contains the enabled attribute which can be set to one of the following values:</span></span>  
  
1.  <span data-ttu-id="2e8b7-111">« None »</span><span class="sxs-lookup"><span data-stu-id="2e8b7-111">"None"</span></span>  
  
2.  <span data-ttu-id="2e8b7-112">« AllExceptIntranet »</span><span class="sxs-lookup"><span data-stu-id="2e8b7-112">"AllExceptIntranet"</span></span>  
  
3.  <span data-ttu-id="2e8b7-113">« Tous »</span><span class="sxs-lookup"><span data-stu-id="2e8b7-113">"All"</span></span>  
  
 <span data-ttu-id="2e8b7-114">Lorsque le paramètre IDN a la valeur « None », aucune conversion est effectuée par Uri.Host ou Uri.DnsSafeHost.</span><span class="sxs-lookup"><span data-stu-id="2e8b7-114">When the IDN setting is set to "None", no conversions are performed by Uri.Host or Uri.DnsSafeHost.</span></span> <span data-ttu-id="2e8b7-115">Lorsque le paramètre IDN a la valeur « Tous », uri. Hôte reste Unicode et l’uri. DnsSafeHost est converti en Punycode.</span><span class="sxs-lookup"><span data-stu-id="2e8b7-115">When the IDN setting is set to "All", uri.Host remains Unicode and uri.DnsSafeHost is converted to Punycode.</span></span> <span data-ttu-id="2e8b7-116">Lorsque le paramètre IDN a la valeur « AllExceptIntranet », les uri. DnsSafeHost est converti en Punycode pour les adresses internet et reste Unicode pour les adresses intranet.</span><span class="sxs-lookup"><span data-stu-id="2e8b7-116">When the IDN setting is set to "AllExceptIntranet", uri.DnsSafeHost is converted to Punycode for internet addresses, and remains Unicode for intranet addresses.</span></span> <span data-ttu-id="2e8b7-117">Ce paramètre est important pour la résolution de noms DNS correcte.</span><span class="sxs-lookup"><span data-stu-id="2e8b7-117">This setting is important for correct DNS name resolution.</span></span> <span data-ttu-id="2e8b7-118">Notez qu'il n'est pas nécessaire de configurer ce paramètres pour Windows 8 et les versions plus récentes.</span><span class="sxs-lookup"><span data-stu-id="2e8b7-118">Note this setting is not required to be configured for Windows 8 and newer versions.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="2e8b7-119">Vous ne devez jamais coder une adresse en dur à l'aide de Punycode.</span><span class="sxs-lookup"><span data-stu-id="2e8b7-119">You should never hard-code an address using Punycode.</span></span> <span data-ttu-id="2e8b7-120">WCF le convertit pour vous en fonction des paramètres de configuration que vous appliquez.</span><span class="sxs-lookup"><span data-stu-id="2e8b7-120">WCF will convert it for you based on the configuration settings you apply.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="2e8b7-121">Lorsque vous ajoutez des caractères Unicode à applicationHost.exe.config, enregistrez le fichier à l'aide de l'encodage UTF-8.</span><span class="sxs-lookup"><span data-stu-id="2e8b7-121">When adding Unicode characters to applicationHost.exe.config, save the file using the UTF-8 encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e8b7-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e8b7-122">See Also</span></span>  
 [<span data-ttu-id="2e8b7-123">System.Uri</span><span class="sxs-lookup"><span data-stu-id="2e8b7-123">System.Uri</span></span>](http://msdn.microsoft.com/library/system.uri.aspx)
