---
title: "Ordre de sérialisation personnalisé avec XmlSerializer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 975abd20-2a1d-42db-aed3-e898025ccce7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ae5969060938763fee63c514de0a87eadbe6537a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="custom-serialization-order-with-xmlserializer"></a><span data-ttu-id="1de4a-102">Ordre de sérialisation personnalisé avec XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="1de4a-102">Custom Serialization Order With XmlSerializer</span></span>
[<span data-ttu-id="1de4a-103">Télécharger l’exemple</span><span class="sxs-lookup"><span data-stu-id="1de4a-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/CustomOrder.zip.exe)  
  
 <span data-ttu-id="1de4a-104">Cet exemple montre comment contrôler l'ordre des éléments sérialisés et désérialisés pour la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="1de4a-104">This sample shows how to control the order of serialized and deserialized elements for XML serialization.</span></span>  
  
 <span data-ttu-id="1de4a-105">Pour plus d'informations sur la sérialisation, consultez les commentaires inclus dans les fichiers de code source et dans les fichiers build-proj.</span><span class="sxs-lookup"><span data-stu-id="1de4a-105">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="1de4a-106">Pour générer l'exemple à partir de l'invite de commandes</span><span class="sxs-lookup"><span data-stu-id="1de4a-106">To build the sample using the Command Prompt</span></span>  
  
1.  <span data-ttu-id="1de4a-107">Ouvrez la fenêtre d'invite de commandes et accédez à l'un des sous-répertoires spécifiques aux différents langages pour l'exemple.</span><span class="sxs-lookup"><span data-stu-id="1de4a-107">Open the Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="1de4a-108">Tapez **msbuild CustomOrder.sln** sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="1de4a-108">Type **msbuild CustomOrder.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="1de4a-109">Pour générer l'exemple à l'aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1de4a-109">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="1de4a-110">Ouvrez l'[!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] et accédez à l'un des sous-répertoires spécifiques aux différents langages de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="1de4a-110">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="1de4a-111">Double-cliquez sur l'icône de CustomOrder.sln pour ouvrir le fichier dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1de4a-111">Double-click the icon for the CustomOrder.sln to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="1de4a-112">Dans le menu **Générer**, sélectionnez **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="1de4a-112">In the **Build** menu, select **Build Solution**.</span></span>  
  
4.  <span data-ttu-id="1de4a-113">L'exemple d'application est généré dans le sous-répertoire \bin ou \bin\Debug par défaut.</span><span class="sxs-lookup"><span data-stu-id="1de4a-113">The sample application is built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1de4a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1de4a-114">See Also</span></span>  
 [<span data-ttu-id="1de4a-115">Sérialisation de base</span><span class="sxs-lookup"><span data-stu-id="1de4a-115">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
 [<span data-ttu-id="1de4a-116">Sérialisation binaire</span><span class="sxs-lookup"><span data-stu-id="1de4a-116">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
 [<span data-ttu-id="1de4a-117">Contrôle de la sérialisation XML à l’aide d’attributs</span><span class="sxs-lookup"><span data-stu-id="1de4a-117">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 [<span data-ttu-id="1de4a-118">Introduction à la sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="1de4a-118">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="1de4a-119">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="1de4a-119">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
 [<span data-ttu-id="1de4a-120">Sérialisation XML et SOAP</span><span class="sxs-lookup"><span data-stu-id="1de4a-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
