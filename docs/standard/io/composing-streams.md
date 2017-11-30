---
title: Composition de flux
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, base streams
- I/O [.NET Framework], composing streams
- Stream class, composing streams
- base streams
- streams, backing stores
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 75800210a52620c5b08a01c5f8fa888bf40843fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="composing-streams"></a><span data-ttu-id="95e96-102">Composition de flux</span><span class="sxs-lookup"><span data-stu-id="95e96-102">Composing Streams</span></span>
<span data-ttu-id="95e96-103">Un magasin de stockage est un support de stockage, tel qu’un disque ou la mémoire.</span><span class="sxs-lookup"><span data-stu-id="95e96-103">A backing store is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="95e96-104">Chaque magasin de stockage implémente son propre flux en tant qu’implémentation de la <xref:System.IO.Stream> classe.</span><span class="sxs-lookup"><span data-stu-id="95e96-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="95e96-105">Chaque type de flux lit et écrit les octets depuis et vers le magasin de sauvegarde donné.</span><span class="sxs-lookup"><span data-stu-id="95e96-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="95e96-106">Flux qui se connectent à sauvegarder des magasins sont appelés des flux de base.</span><span class="sxs-lookup"><span data-stu-id="95e96-106">Streams that connect to backing stores are called base streams.</span></span> <span data-ttu-id="95e96-107">Flux de base possèdent des constructeurs qui ont les paramètres requis pour connecter le flux au magasin de stockage.</span><span class="sxs-lookup"><span data-stu-id="95e96-107">Base streams have constructors that have the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="95e96-108">Par exemple, <xref:System.IO.FileStream> a des constructeurs qui spécifient un paramètre de chemin d’accès, qui indique la façon dont le fichier est partagé par les processus et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="95e96-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes, and so on.</span></span>  
  
 <span data-ttu-id="95e96-109">La conception de le <xref:System.IO> fournit des classes de composition simplifiée des flux.</span><span class="sxs-lookup"><span data-stu-id="95e96-109">The design of the <xref:System.IO> classes provides simplified stream composing.</span></span> <span data-ttu-id="95e96-110">Flux de base pouvant être joints à un ou plusieurs flux directs qui fournissent la fonctionnalité souhaitée.</span><span class="sxs-lookup"><span data-stu-id="95e96-110">Base streams can be attached to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="95e96-111">Un lecteur ou un writer peut être attaché à la fin de la chaîne afin que les types par défaut peuvent être lues ou écrites facilement.</span><span class="sxs-lookup"><span data-stu-id="95e96-111">A reader or writer can be attached to the end of the chain so that the preferred types can be read or written easily.</span></span>  
  
 <span data-ttu-id="95e96-112">L’exemple de code suivant crée un **FileStream** autour existants `MyFile.txt` dans l’ordre de la mémoire tampon `MyFile.txt`.</span><span class="sxs-lookup"><span data-stu-id="95e96-112">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="95e96-113">(Notez que **FileStreams** sont mis en mémoire tampon par défaut.) Ensuite, un <xref:System.IO.StreamReader> est créé pour lire des caractères à partir de la **FileStream**, qui est transmis à la **StreamReader** en tant qu’argument de son constructeur.</span><span class="sxs-lookup"><span data-stu-id="95e96-113">(Note that **FileStreams** are buffered by default.) Next, a <xref:System.IO.StreamReader> is created to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="95e96-114"><xref:System.IO.StreamReader.ReadLine%2A>lit jusqu'à ce que <xref:System.IO.StreamReader.Peek%2A> détecte plus aucun caractère.</span><span class="sxs-lookup"><span data-stu-id="95e96-114"><xref:System.IO.StreamReader.ReadLine%2A> reads until <xref:System.IO.StreamReader.Peek%2A> finds no more characters.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 <span data-ttu-id="95e96-115">L’exemple de code suivant crée un **FileStream** autour existants `MyFile.txt` dans l’ordre de la mémoire tampon `MyFile.txt`.</span><span class="sxs-lookup"><span data-stu-id="95e96-115">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="95e96-116">(Notez que **FileStreams** sont mis en mémoire tampon par défaut.) Ensuite, un **BinaryReader** est créé pour lire les octets à partir de la **FileStream**, qui est transmis à la **BinaryReader** en tant qu’argument de son constructeur.</span><span class="sxs-lookup"><span data-stu-id="95e96-116">(Note that **FileStreams** are buffered by default.) Next, a **BinaryReader** is created to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="95e96-117"><xref:System.IO.BinaryReader.ReadByte%2A>lit jusqu'à ce que <xref:System.IO.BinaryReader.PeekChar%2A> détecte plus aucun octet.</span><span class="sxs-lookup"><span data-stu-id="95e96-117"><xref:System.IO.BinaryReader.ReadByte%2A> reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="95e96-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95e96-118">See Also</span></span>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
 <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
