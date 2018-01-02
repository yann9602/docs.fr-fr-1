---
title: "&lt;configSections&gt; , élément pour &lt;configuration&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 145a2a5cc23758c9fd2211c2da7fee0bbd736f0f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="e0dba-102">\<configSections >, élément pour \<configuration ></span><span class="sxs-lookup"><span data-stu-id="e0dba-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="e0dba-103">Contient des déclarations d’espace de noms et de la section de configuration.</span><span class="sxs-lookup"><span data-stu-id="e0dba-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="e0dba-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e0dba-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="e0dba-105">&nbsp;&nbsp;**\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="e0dba-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="e0dba-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="e0dba-106">Attributes</span></span>

<span data-ttu-id="e0dba-107">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e0dba-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="e0dba-108">Élément parent</span><span class="sxs-lookup"><span data-stu-id="e0dba-108">Parent element</span></span>

|     | <span data-ttu-id="e0dba-109">Description</span><span class="sxs-lookup"><span data-stu-id="e0dba-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e0dba-110">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="e0dba-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="e0dba-111">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e0dba-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="e0dba-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e0dba-112">Child elements</span></span>

|     | <span data-ttu-id="e0dba-113">Description</span><span class="sxs-lookup"><span data-stu-id="e0dba-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e0dba-114">**\<section >**</span><span class="sxs-lookup"><span data-stu-id="e0dba-114">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="e0dba-115">Contient une déclaration de section de configuration.</span><span class="sxs-lookup"><span data-stu-id="e0dba-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="e0dba-116">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="e0dba-116">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="e0dba-117">Définit un espace de noms de sections de configuration.</span><span class="sxs-lookup"><span data-stu-id="e0dba-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="e0dba-118">**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="e0dba-118">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="e0dba-119">Supprime un groupe de sections ou une section prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="e0dba-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="e0dba-120">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="e0dba-120">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="e0dba-121">Efface toutes les sections précédemment définies et des groupes.</span><span class="sxs-lookup"><span data-stu-id="e0dba-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="e0dba-122">Notes</span><span class="sxs-lookup"><span data-stu-id="e0dba-122">Remarks</span></span>

<span data-ttu-id="e0dba-123">Si cet élément est dans un fichier de configuration, il doit être le premier élément enfant de le  **\<configuration >** élément.</span><span class="sxs-lookup"><span data-stu-id="e0dba-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="e0dba-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="e0dba-124">Example</span></span>

<span data-ttu-id="e0dba-125">L’exemple suivant montre comment définir une section de configuration et de définir les paramètres de cette section :</span><span class="sxs-lookup"><span data-stu-id="e0dba-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="e0dba-126">fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="e0dba-126">Configuration file</span></span>

<span data-ttu-id="e0dba-127">Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration machine (*Machine.config*), et *Web.config* les fichiers qui ne sont pas au niveau du répertoire d’application.</span><span class="sxs-lookup"><span data-stu-id="e0dba-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0dba-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0dba-128">See also</span></span>

[<span data-ttu-id="e0dba-129">Schéma de fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e0dba-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
