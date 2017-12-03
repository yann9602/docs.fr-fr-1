---
title: '&lt;comContracts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1be69cea2b6e47ae10652e3d59936836bb6d1653
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcomcontractsgt"></a><span data-ttu-id="8507b-102">&lt;comContracts&gt;</span><span class="sxs-lookup"><span data-stu-id="8507b-102">&lt;comContracts&gt;</span></span>
<span data-ttu-id="8507b-103">La section de configuration `comContracts` contient des éléments qui vous permettent de spécifier différentes propriétés d'un contrat de service d'intégration COM+.</span><span class="sxs-lookup"><span data-stu-id="8507b-103">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="8507b-104">Spécification d'espace de noms et de contrat</span><span class="sxs-lookup"><span data-stu-id="8507b-104">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="8507b-105">Contrats de service d’intégration COM + sont actuellement restreints à l’espace de noms « http://tempuri.org » et le nom de contrat est dérivé de l’interface COM de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="8507b-105">COM+ integration service contracts are currently restricted to the "http://tempuri.org" namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="8507b-106">Toutefois, vous pouvez en spécifier d'autres à l'aide de la section `comContracts` du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="8507b-106">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="8507b-107">Par exemple, vous pouvez utiliser la configuration suivante pour spécifier l'espace de noms et le nom du contrat de service, aussi bien qu'une option pour mettre en vigueur l'utilisation sur les liaisons de session.</span><span class="sxs-lookup"><span data-stu-id="8507b-107">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
  </comContract>  
</comContracts>  
```  
  
 <span data-ttu-id="8507b-108">Lorsque le service est initialisé, les espaces de noms et les noms de contrat spécifiés sont appliqués aux descriptions de service générées.</span><span class="sxs-lookup"><span data-stu-id="8507b-108">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="8507b-109">Lorsque cette section est vide, l'initialisation de service applique un espace de noms et un nom de contrat par défaut à partir de l'ID d'interface COM de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="8507b-109">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="8507b-110">En outre, vous pouvez utiliser la [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) élément pour spécifier les méthodes COM + exposées lorsque l’interface sur un composant COM + est exposée comme un service Web.</span><span class="sxs-lookup"><span data-stu-id="8507b-110">In addition, you can use the [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="8507b-111">Vous pouvez également utiliser le [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) pour spécifier les types persistants utilisés dans l’intégration.</span><span class="sxs-lookup"><span data-stu-id="8507b-111">You can also use the [\<persistableTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="8507b-112">Enfin, vous pouvez utiliser la [ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) élément à inclure défini Types utilisateur (UDT) qui doivent être inclus dans le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="8507b-112">Finally, you can use the [\<userDefinedType>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8507b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8507b-113">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="8507b-114">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="8507b-114">\<exposedMethod></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [<span data-ttu-id="8507b-115">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="8507b-115">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [<span data-ttu-id="8507b-116">\<userDefinedType ></span><span class="sxs-lookup"><span data-stu-id="8507b-116">\<userDefinedType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [<span data-ttu-id="8507b-117">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="8507b-117">\<comContract></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [<span data-ttu-id="8507b-118">Intégration à des Applications COM +</span><span class="sxs-lookup"><span data-stu-id="8507b-118">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="8507b-119">Comment : configurer les paramètres de Service COM +</span><span class="sxs-lookup"><span data-stu-id="8507b-119">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
