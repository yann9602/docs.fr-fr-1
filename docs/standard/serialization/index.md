---
title: "Sérialisation dans .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1a0d9f5fd32b5610e3d7b05455c7bd3c55b5b77e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="serialization-in-net"></a><span data-ttu-id="a22a3-102">Sérialisation dans .NET</span><span class="sxs-lookup"><span data-stu-id="a22a3-102">Serialization in .NET</span></span>
<span data-ttu-id="a22a3-103">La sérialisation correspond au processus de conversion de l'état d'un objet en un formulaire persistant ou transportable.</span><span class="sxs-lookup"><span data-stu-id="a22a3-103">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="a22a3-104">Le complément de la sérialisation est la désérialisation, qui convertit un flux de données en un objet.</span><span class="sxs-lookup"><span data-stu-id="a22a3-104">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="a22a3-105">Ces deux processus permettent de stocker et de transférer facilement des données.</span><span class="sxs-lookup"><span data-stu-id="a22a3-105">Together, these processes allow data to be easily stored and transferred.</span></span>  
  
<span data-ttu-id="a22a3-106">.NET comprend deux technologies de sérialisation :</span><span class="sxs-lookup"><span data-stu-id="a22a3-106">.NET features two serialization technologies:</span></span>  
  
-   <span data-ttu-id="a22a3-107">La sérialisation binaire préserve le respect des types, qui permet de conserver l'état d'un objet entre plusieurs appels d'une application.</span><span class="sxs-lookup"><span data-stu-id="a22a3-107">Binary serialization preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="a22a3-108">Par exemple, vous pouvez partager un objet entre plusieurs applications en le sérialisant dans le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="a22a3-108">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="a22a3-109">Vous pouvez sérialiser un objet vers un flux, un disque, la mémoire, le réseau, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="a22a3-109">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="a22a3-110">La communication à distance utilise la sérialisation pour passer des objets « par valeur » d'un ordinateur ou d'un domaine d'application à un autre.</span><span class="sxs-lookup"><span data-stu-id="a22a3-110">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
-   <span data-ttu-id="a22a3-111">La sérialisation XML sérialise uniquement des propriétés et des champs publics mais ne conserve pas le respect des types.</span><span class="sxs-lookup"><span data-stu-id="a22a3-111">XML serialization serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="a22a3-112">Ceci est utile lorsque vous souhaitez fournir ou consommer des données sans restreindre l'application qui les utilise.</span><span class="sxs-lookup"><span data-stu-id="a22a3-112">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="a22a3-113">XML étant une norme ouverte, elle constitue une option intéressante pour partager des données via le Web.</span><span class="sxs-lookup"><span data-stu-id="a22a3-113">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="a22a3-114">Le protocole SOAP est également une norme ouverte et représente par conséquent une option avantageuse.</span><span class="sxs-lookup"><span data-stu-id="a22a3-114">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a22a3-115">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a22a3-115">In This Section</span></span>  
[<span data-ttu-id="a22a3-116">Rubriques de guides pratiques pour la sérialisation</span><span class="sxs-lookup"><span data-stu-id="a22a3-116">Serialization How-to Topics</span></span>](../../../docs/standard/serialization/serialization-how-to-topics.md)  
<span data-ttu-id="a22a3-117">Répertorie les liens vers les rubriques Comment contenues dans cette section.</span><span class="sxs-lookup"><span data-stu-id="a22a3-117">Lists links to How-to topics contained in this section.</span></span>
  
[<span data-ttu-id="a22a3-118">Sérialisation binaire</span><span class="sxs-lookup"><span data-stu-id="a22a3-118">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
<span data-ttu-id="a22a3-119">Décrit le mécanisme de sérialisation binaire inclus avec le Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="a22a3-119">Describes the binary serialization mechanism that is included with the common language runtime.</span></span>

[<span data-ttu-id="a22a3-120">Sérialisation XML et SOAP</span><span class="sxs-lookup"><span data-stu-id="a22a3-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
<span data-ttu-id="a22a3-121">Décrit le mécanisme de sérialisation XML et SOAP inclus avec le Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="a22a3-121">Describes the XML and SOAP serialization mechanism that is included with the common language runtime.</span></span>

[<span data-ttu-id="a22a3-122">Outils de sérialisation</span><span class="sxs-lookup"><span data-stu-id="a22a3-122">Serialization Tools</span></span>](../../../docs/standard/serialization/serialization-tools.md)  
<span data-ttu-id="a22a3-123">Ces outils vous aident à développer le code de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="a22a3-123">These tools help develop serialization code.</span></span>

[<span data-ttu-id="a22a3-124">Exemples de sérialisation</span><span class="sxs-lookup"><span data-stu-id="a22a3-124">Serialization Samples</span></span>](../../../docs/standard/serialization/serialization-samples.md)  
<span data-ttu-id="a22a3-125">Les exemples montrent comment procéder à la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="a22a3-125">The samples demonstrate how to do serialization.</span></span>

## <a name="reference"></a><span data-ttu-id="a22a3-126">Référence</span><span class="sxs-lookup"><span data-stu-id="a22a3-126">Reference</span></span>
<span data-ttu-id="a22a3-127"><xref:System.Runtime.Serialization> contient des classes qui peuvent être utilisées pour sérialiser et désérialiser des objets.</span><span class="sxs-lookup"><span data-stu-id="a22a3-127"><xref:System.Runtime.Serialization> Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="a22a3-128">Contient des classes qui peuvent être utilisées pour sérialiser des objets en documents ou en flux de données au format XML.</span><span class="sxs-lookup"><span data-stu-id="a22a3-128">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>