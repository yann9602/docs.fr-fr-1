---
title: "&lt;IDN&gt; élément (paramètres d’Uri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 44e2db95ec354fff4356a3619fa8230faf67544d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltidngt-element-uri-settings"></a><span data-ttu-id="83382-102">&lt;IDN&gt; élément (paramètres d’Uri)</span><span class="sxs-lookup"><span data-stu-id="83382-102">&lt;idn&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="83382-103">Spécifie si l’analyse de nom de domaine internationaux (IDN) est appliqué à un nom de domaine.</span><span class="sxs-lookup"><span data-stu-id="83382-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="83382-104">Hiérarchie de schéma</span><span class="sxs-lookup"><span data-stu-id="83382-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="83382-105">\<configuration>, élément</span><span class="sxs-lookup"><span data-stu-id="83382-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="83382-106">\<URI >, élément (paramètres d’Uri)</span><span class="sxs-lookup"><span data-stu-id="83382-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="83382-107">\<IDN ></span><span class="sxs-lookup"><span data-stu-id="83382-107">\<idn></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="83382-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83382-108">Syntax</span></span>  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83382-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="83382-109">Attributes and Elements</span></span>  
 <span data-ttu-id="83382-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="83382-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83382-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="83382-111">Attributes</span></span>  
  
|<span data-ttu-id="83382-112">**Élément**</span><span class="sxs-lookup"><span data-stu-id="83382-112">**Element**</span></span>|<span data-ttu-id="83382-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="83382-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="83382-114">Spécifie que si l’analyse de nom de domaine internationaux (IDN) est appliqué à un nom de domaine la valeur par défaut est none.</span><span class="sxs-lookup"><span data-stu-id="83382-114">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83382-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="83382-115">Child Elements</span></span>  
 <span data-ttu-id="83382-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="83382-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83382-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="83382-117">Parent Elements</span></span>  
  
|<span data-ttu-id="83382-118">**Élément**</span><span class="sxs-lookup"><span data-stu-id="83382-118">**Element**</span></span>|<span data-ttu-id="83382-119">**Description**</span><span class="sxs-lookup"><span data-stu-id="83382-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="83382-120">URI</span><span class="sxs-lookup"><span data-stu-id="83382-120">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="83382-121">Contient des paramètres qui spécifient la façon dont le .NET Framework gère les adresses web exprimées à l’aide d’identificateurs de ressource uniforme (URI).</span><span class="sxs-lookup"><span data-stu-id="83382-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83382-122">Notes</span><span class="sxs-lookup"><span data-stu-id="83382-122">Remarks</span></span>  
 <span data-ttu-id="83382-123">Existants <xref:System.Uri> classe a été étendue dans .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="83382-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="83382-124">3.0 SP1 et 2.0 SP1 avec prise en charge pour les identificateurs IRI (International Resource) et les noms de domaine internationaux (IDN).</span><span class="sxs-lookup"><span data-stu-id="83382-124">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="83382-125">Les utilisateurs actuels ne verront pas de toute modification du comportement de .NET Framework 2.0, à moins qu’ils activent spécifiquement IRI et IDN prennent en charge.</span><span class="sxs-lookup"><span data-stu-id="83382-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="83382-126">Cela garantit la compatibilité des applications avec les versions antérieures de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="83382-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="83382-127">Pour activer la prise en charge des IRI, les deux modifications suivantes sont requises :</span><span class="sxs-lookup"><span data-stu-id="83382-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="83382-128">Ajoutez la ligne suivante au fichier machine.config sous le répertoire .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="83382-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="83382-129">Spécifiez si vous souhaitez que l’analyse de nom de domaine internationaux (IDN) appliquée au nom de domaine et si les règles d’analyse ini doit être appliquée.</span><span class="sxs-lookup"><span data-stu-id="83382-129">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="83382-130">Cela est spécifié dans le fichier machine.config ou app.config.</span><span class="sxs-lookup"><span data-stu-id="83382-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="83382-131">Il existe trois valeurs possibles pour l’IDN selon les serveurs DNS qui sont utilisés :</span><span class="sxs-lookup"><span data-stu-id="83382-131">There are three possible values for IDN depending on the DNS servers that are used:</span></span>  
  
-   <span data-ttu-id="83382-132">IDN activé = All</span><span class="sxs-lookup"><span data-stu-id="83382-132">idn enabled = All</span></span>  
  
     <span data-ttu-id="83382-133">Cette valeur convertit tous les noms de domaine Unicode en leurs équivalents Punycode (noms IDN).</span><span class="sxs-lookup"><span data-stu-id="83382-133">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>  
  
-   <span data-ttu-id="83382-134">IDN activé = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="83382-134">idn enabled = AllExceptIntranet</span></span>  
  
     <span data-ttu-id="83382-135">Cette valeur convertit tous les noms de domaine Unicode pas sur l’Intranet local pour utiliser les équivalents Punycode (noms IDN).</span><span class="sxs-lookup"><span data-stu-id="83382-135">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="83382-136">Dans ce cas pour gérer des noms internationaux sur l’Intranet local, les serveurs DNS qui sont utilisés pour l’Intranet doivent prendre en charge la résolution de noms Unicode.</span><span class="sxs-lookup"><span data-stu-id="83382-136">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>  
  
-   <span data-ttu-id="83382-137">IDN activé = None</span><span class="sxs-lookup"><span data-stu-id="83382-137">idn enabled = None</span></span>  
  
     <span data-ttu-id="83382-138">Cette valeur ne convertira pas tous les noms de domaine Unicode pour utiliser Punycode.</span><span class="sxs-lookup"><span data-stu-id="83382-138">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="83382-139">Il s’agit de la valeur par défaut qui est cohérente avec le comportement de .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="83382-139">This is the default value which is consistent with the .NET Framework 2.0 behaviour.</span></span>  
  
 <span data-ttu-id="83382-140">L’activation des IDN entraîne la conversion de toutes les étiquettes Unicode d’un nom de domaine en leurs équivalents Punycode.</span><span class="sxs-lookup"><span data-stu-id="83382-140">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="83382-141">Les noms Punycode contiennent uniquement des caractères ASCII et commencent toujours par le préfixe xn--.</span><span class="sxs-lookup"><span data-stu-id="83382-141">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="83382-142">Cela permet de garantir la prise en charge des serveurs DNS existants sur Internet, la plupart d’entre eux prenant uniquement en charge les caractères ASCII (consultez la norme RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="83382-142">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="83382-143">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="83382-143">Configuration Files</span></span>  
 <span data-ttu-id="83382-144">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="83382-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="83382-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="83382-145">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="83382-146">Description</span><span class="sxs-lookup"><span data-stu-id="83382-146">Description</span></span>  
 <span data-ttu-id="83382-147">L’exemple suivant montre une configuration utilisée par la <xref:System.Uri> classe pour prendre en charge l’analyse IRI et les noms IDN.</span><span class="sxs-lookup"><span data-stu-id="83382-147">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="83382-148">Code</span><span class="sxs-lookup"><span data-stu-id="83382-148">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="83382-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83382-149">See Also</span></span>  
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [<span data-ttu-id="83382-150">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="83382-150">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
