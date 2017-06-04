---
title: "Composition de flux | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "flux, flux de base"
  - "E/S (.NET Framework), composer des flux"
  - "classe Stream, composer des flux"
  - "flux de base"
  - "flux, sauvegarder des magasins"
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# Composition de flux
Un magasin de stockage correspond à un support de stockage tel qu'un disque ou la mémoire.  Chaque magasin de stockage implémente son propre flux en tant qu'implémentation de la classe <xref:System.IO.Stream>.  Chaque type de flux lit les octets à partir de son magasin de stockage donné ou les y écrit.  Les flux qui se connectent à des magasins de stockage sont appelés flux de base.  Les flux de base possèdent des constructeurs qui ont les paramètres requis pour connecter le flux au magasin de stockage.  Par exemple, <xref:System.IO.FileStream> possède des constructeurs spécifiant un paramètre de chemin d'accès, qui indique le mode de partage du fichier par les processus, etc.  
  
 Le design des classes <xref:System.IO> assure une composition simplifiée des flux.  Les flux de base peuvent être associés à un ou plusieurs flux directs fournissant la fonctionnalité souhaitée.  Un lecteur ou un writer peut être attaché en fin de chaîne afin de pouvoir aisément lire ou écrire les types préférés.  
  
 L'exemple de code suivant crée **FileStream** à partir du fichier `MyFile.txt` existant afin de placer `MyFile.txt` en mémoire tampon. \(Notez que les objets **FileStream** sont mis par défaut en mémoire tampon.\) Ensuite, un <xref:System.IO.StreamReader> est créé pour lire des caractères de **FileStream**, passé au **StreamReader** comme son argument de constructeur.  <xref:System.IO.StreamReader.ReadLine%2A> lit jusqu'à ce que <xref:System.IO.StreamReader.Peek%2A> ne trouve plus de caractères.  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 L'exemple de code suivant crée **FileStream** à partir du fichier `MyFile.txt` existant afin de placer `MyFile.txt` en mémoire tampon. \(Notez que les objets **FileStream** sont mis par défaut en mémoire tampon.\) Ensuite, un **BinaryReader** est créé pour lire des octets du **FileStream**, passé au **BinaryReader** comme son argument de constructeur.  <xref:System.IO.BinaryReader.ReadByte%2A> lit jusqu'à ce que <xref:System.IO.BinaryReader.PeekChar%2A> ne trouve plus d'octets.  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## Voir aussi  
 <xref:System.IO.StreamReader>   
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName>   
 <xref:System.IO.StreamReader.Peek%2A?displayProperty=fullName>   
 <xref:System.IO.FileStream>   
 <xref:System.IO.BinaryReader>   
 <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=fullName>   
 <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=fullName>