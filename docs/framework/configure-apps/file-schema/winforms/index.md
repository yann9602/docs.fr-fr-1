---
title: Section de configuration de Windows Forms
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b83f00f82de727812c5737915a6dc35ec98e4734
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="b47ce-102">Section de configuration de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b47ce-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="b47ce-103">Les paramètres de configuration de Windows Forms permettent à une application Windows Forms de stocker et d’extraire des informations sur les paramètres d’application personnalisés, par exemple la prise en charge de plusieurs écrans, la prise en charge de la haute résolution et d’autres paramètres de configuration prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="b47ce-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="b47ce-104">Les paramètres de configuration de l’application Windows Forms sont stockés dans l’élément `System.Windows.Forms.ApplicationConfigurationSection` d’un fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="b47ce-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="b47ce-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b47ce-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b47ce-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b47ce-106">Attributes and elements</span></span>

<span data-ttu-id="b47ce-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b47ce-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b47ce-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="b47ce-108">Attributes</span></span>

<span data-ttu-id="b47ce-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b47ce-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b47ce-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b47ce-110">Child elements</span></span>

<span data-ttu-id="b47ce-111">Élément</span><span class="sxs-lookup"><span data-stu-id="b47ce-111">Element</span></span>  |<span data-ttu-id="b47ce-112">Description</span><span class="sxs-lookup"><span data-stu-id="b47ce-112">Description</span></span> |
---------|---------|
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | <span data-ttu-id="b47ce-113">Ajoute une clé de paramètre de configuration avec une valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b47ce-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="b47ce-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b47ce-114">Parent elements</span></span>

<span data-ttu-id="b47ce-115">Élément</span><span class="sxs-lookup"><span data-stu-id="b47ce-115">Element</span></span>  |<span data-ttu-id="b47ce-116">Description</span><span class="sxs-lookup"><span data-stu-id="b47ce-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="b47ce-117">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b47ce-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="b47ce-118">Élément racine de chaque fichier de configuration utilisé par le common language runtime et les applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b47ce-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="b47ce-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="b47ce-119">Remarks</span></span>

<span data-ttu-id="b47ce-120">À compter du .NET Framework 4.7, l’élément `<System.Windows.Forms.ApplicationConfigurationSection>` vous permet de configurer des applications Windows Forms pour tirer parti des fonctionnalités ajoutées dans les dernières versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b47ce-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="b47ce-121">L’élément `<System.Windows.Forms.ApplicationConfigurationSection>` peut contenir un ou plusieurs éléments [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) enfants, dont chacun définit un paramètre de configuration spécifique.</span><span class="sxs-lookup"><span data-stu-id="b47ce-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="b47ce-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b47ce-122">See also</span></span>

<span data-ttu-id="b47ce-123">[Schéma des fichiers de configuration](../index.md) </span><span class="sxs-lookup"><span data-stu-id="b47ce-123">[Configuration File Schema](../index.md) </span></span>  
[<span data-ttu-id="b47ce-124">Prise en charge de la haute résolution dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b47ce-124">High DPI Support in Windows Forms</span></span>](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
