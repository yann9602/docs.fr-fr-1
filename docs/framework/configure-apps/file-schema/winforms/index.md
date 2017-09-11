---
title: Section de configuration de Windows Forms | Microsoft Docs
ms.custom: 
ms.date: 04/07/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
ms.translationtype: Human Translation
ms.sourcegitcommit: 39e8e757a446b30ab18914465853138e1c239e40
ms.openlocfilehash: dedf9497a684c4b11f84b60de21ec73b563c6d19
ms.contentlocale: fr-fr
ms.lasthandoff: 05/03/2017

---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="6f5fe-102">Section de configuration de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6f5fe-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="6f5fe-103">Les paramètres de configuration de Windows Forms permettent à une application Windows Forms de stocker et d’extraire des informations sur les paramètres d’application personnalisés, par exemple la prise en charge de plusieurs écrans, la prise en charge de la haute résolution et d’autres paramètres de configuration prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="6f5fe-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="6f5fe-104">Les paramètres de configuration de l’application Windows Forms sont stockés dans l’élément `System.Windows.Forms.ConfigurationSection` d’un fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="6f5fe-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="6f5fe-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f5fe-105">Syntax</span></span>

```xml
<configuration>
  \<System.Windows.Forms.ConfigurationSection>
  ...
  \</System.Windows.Forms.ConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6f5fe-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6f5fe-106">Attributes and elements</span></span>

<span data-ttu-id="6f5fe-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6f5fe-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6f5fe-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="6f5fe-108">Attributes</span></span>

<span data-ttu-id="6f5fe-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6f5fe-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6f5fe-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6f5fe-110">Child elements</span></span>

<span data-ttu-id="6f5fe-111">Élément</span><span class="sxs-lookup"><span data-stu-id="6f5fe-111">Element</span></span>  |<span data-ttu-id="6f5fe-112">Description</span><span class="sxs-lookup"><span data-stu-id="6f5fe-112">Description</span></span> |
---------|---------|
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | <span data-ttu-id="6f5fe-113">Ajoute une clé de paramètre de configuration avec une valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6f5fe-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="6f5fe-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6f5fe-114">Parent elements</span></span>

<span data-ttu-id="6f5fe-115">Élément</span><span class="sxs-lookup"><span data-stu-id="6f5fe-115">Element</span></span>  |<span data-ttu-id="6f5fe-116">Description</span><span class="sxs-lookup"><span data-stu-id="6f5fe-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="6f5fe-117">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6f5fe-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="6f5fe-118">Élément racine de chaque fichier de configuration utilisé par le common language runtime et les applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6f5fe-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="6f5fe-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="6f5fe-119">Remarks</span></span>

<span data-ttu-id="6f5fe-120">À compter du .NET Framework 4.7, l’élément `<System.Windows.Forms.ConfigurationSection>` vous permet de configurer des applications Windows Forms pour tirer parti des fonctionnalités ajoutées dans les dernières versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6f5fe-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="6f5fe-121">L’élément `<System.Windows.Forms.ConfigurationSection>` peut contenir un ou plusieurs éléments [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) enfants, dont chacun définit un paramètre de configuration spécifique.</span><span class="sxs-lookup"><span data-stu-id="6f5fe-121">The `<System.Windows.Forms.ConfigurationSection>` element can include one or more child [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f5fe-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f5fe-122">See also</span></span>

<span data-ttu-id="6f5fe-123">[Schéma du fichier de configuration](../index.md)
[Prise en charge de la haute résolution dans Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="6f5fe-123">[Configuration File Schema](../index.md)
[High DPI Support in Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)</span></span>

