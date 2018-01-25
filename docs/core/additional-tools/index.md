---
title: "Outils .NET Core supplémentaires"
description: "Vue d’ensemble des outils supplémentaires qui prennent en charge et étendent les fonctionnalités de .NET Core."
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2018
ms.topic: article
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: 21fcc1190ee4586a8d7eb6fb8d63a7c312e63825
ms.sourcegitcommit: c1904b0437605a90e5aa65b4abd7e048000e349d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2018
---
# <a name="net-core-additional-tools"></a><span data-ttu-id="f70a3-103">Outils .NET Core supplémentaires</span><span class="sxs-lookup"><span data-stu-id="f70a3-103">.NET Core additional tools</span></span>

<span data-ttu-id="f70a3-104">Cette section dresse une liste des outils qui prennent en charge et étendent les fonctionnalités de .NET Core, en plus des outils d’[interface de ligne de commande (CLI) .NET Core](..\tools\index.md).</span><span class="sxs-lookup"><span data-stu-id="f70a3-104">This section compiles a list of tools that support and extend the .NET Core functionality, in addition to the [.NET Core command-line interface (CLI)](..\tools\index.md) tools.</span></span>

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[<span data-ttu-id="f70a3-105">Outil WCF Web Service Reference</span><span class="sxs-lookup"><span data-stu-id="f70a3-105">WCF Web Service Reference Tool</span></span>](wcf-web-service-reference-guide.md)

<span data-ttu-id="f70a3-106">WCF Web Service Reference est un fournisseur de services connectés Visual Studio qui a fait son apparition dans [Visual Studio 2017 version 15.5](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#WCFTools).</span><span class="sxs-lookup"><span data-stu-id="f70a3-106">The WCF Web Service Reference is a Visual Studio connected service provider that made its debut in [Visual Studio 2017 version 15.5](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#WCFTools).</span></span> <span data-ttu-id="f70a3-107">Cet outil récupère les métadonnées d’un service web dans la solution actuelle sur un emplacement réseau ou dans un fichier WSDL, puis génère un fichier source compatible .NET Core contenant du code de proxy client WCF (Windows Communication Foundation) que vous pouvez utiliser pour accéder au service web.</span><span class="sxs-lookup"><span data-stu-id="f70a3-107">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[<span data-ttu-id="f70a3-108">Générateur de sérialiseur XML</span><span class="sxs-lookup"><span data-stu-id="f70a3-108">XML Serializer Generator</span></span>](xml-serializer-generator.md)

<span data-ttu-id="f70a3-109">Comme le [Générateur de sérialiseur XML (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pour le .NET Framework, le [package NuGet Microsoft.XmlSerializer.Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) est la solution pour les bibliothèques .NET Core et .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="f70a3-109">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the solution for .NET Core and .NET Standard libraries.</span></span> <span data-ttu-id="f70a3-110">Il crée un assembly de sérialisation XML pour les types contenus dans un assembly afin d’améliorer les performances de démarrage de la sérialisation XML pendant la sérialisation ou la désérialisation des objets de ces types avec <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f70a3-110">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>