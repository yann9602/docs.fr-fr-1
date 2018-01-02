---
title: "&lt;Désactivez&gt; , élément de schemeSettings (paramètres d’Uri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: ffbe875e99376a7c782f177438709bcbb0ccb528
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="0e798-102">&lt;Désactivez&gt; , élément de schemeSettings (paramètres d’Uri)</span><span class="sxs-lookup"><span data-stu-id="0e798-102">&lt;clear&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="0e798-103">Efface tous les paramètres de modèle existant.</span><span class="sxs-lookup"><span data-stu-id="0e798-103">Clears all existing scheme settings.</span></span>  
  
 <span data-ttu-id="0e798-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0e798-104">\<configuration></span></span>  
<span data-ttu-id="0e798-105">\<URI ></span><span class="sxs-lookup"><span data-stu-id="0e798-105">\<uri></span></span>  
<span data-ttu-id="0e798-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="0e798-106">\<schemeSettings></span></span>  
<span data-ttu-id="0e798-107">\<Désactivez ></span><span class="sxs-lookup"><span data-stu-id="0e798-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e798-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e798-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e798-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0e798-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0e798-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0e798-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e798-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="0e798-111">Attributes</span></span>  
 <span data-ttu-id="0e798-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0e798-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0e798-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0e798-113">Child Elements</span></span>  
 <span data-ttu-id="0e798-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0e798-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0e798-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0e798-115">Parent Elements</span></span>  
  
|<span data-ttu-id="0e798-116">Élément</span><span class="sxs-lookup"><span data-stu-id="0e798-116">Element</span></span>|<span data-ttu-id="0e798-117">Description</span><span class="sxs-lookup"><span data-stu-id="0e798-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e798-118">\<schemeSettings, élément (paramètres d’Uri)</span><span class="sxs-lookup"><span data-stu-id="0e798-118">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="0e798-119">Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.</span><span class="sxs-lookup"><span data-stu-id="0e798-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e798-120">Notes</span><span class="sxs-lookup"><span data-stu-id="0e798-120">Remarks</span></span>  
 <span data-ttu-id="0e798-121">Par défaut, le <xref:System.Uri?displayProperty=nameWithType> pour cent de classe n’échappe pas encodée séparateurs de chemin d’accès avant d’exécuter la compression de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="0e798-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="0e798-122">Cela a été implémenté en tant que mécanisme de sécurité contre les attaques comme suit :</span><span class="sxs-lookup"><span data-stu-id="0e798-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="0e798-123">Si cet URI est passé à des modules ne gère ne pas % correctement les caractères encodés, elle peut entraîner la commande suivante, exécutée par le serveur :</span><span class="sxs-lookup"><span data-stu-id="0e798-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="0e798-124">Pour cette raison, <xref:System.Uri?displayProperty=nameWithType> première séparateurs de chemin d’accès n’échappe pas de classe, puis applique la compression de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="0e798-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="0e798-125">Le résultat du passage de l’URL malveillante ci-dessus pour <xref:System.Uri?displayProperty=nameWithType> classe constructeur se traduit par l’URI suivant :</span><span class="sxs-lookup"><span data-stu-id="0e798-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="0e798-126">Ce comportement par défaut peut être modifié pour ne pas les délimiteurs de chemin d’accès codé en pourcentage échapper à l’aide de l’option de configuration schemeSettings pour un modèle spécifique.</span><span class="sxs-lookup"><span data-stu-id="0e798-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0e798-127">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="0e798-127">Configuration Files</span></span>  
 <span data-ttu-id="0e798-128">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="0e798-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e798-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="0e798-129">Example</span></span>  
 <span data-ttu-id="0e798-130">L’exemple suivant montre une configuration utilisée par la <xref:System.Uri> classe qui efface tous les paramètres de modèle, puis ajoute la prise en charge pour l’échappement ne pas les séparateurs de chemin d’accès encodés en pourcentage pour le schéma http.</span><span class="sxs-lookup"><span data-stu-id="0e798-130">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e798-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e798-131">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="0e798-132">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="0e798-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
