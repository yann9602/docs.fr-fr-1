---
title: "Guide pratique pour segmenter des données sérialisées"
ms.date: 03/30/2017
ms.prod: .net
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- chunking serialized data
- data chunking
- binary serialization, chunking data
- large data set chunking
- serialization, chunking data
- serialization, examples
- binary serialization, examples
ms.assetid: 22f1b818-7e0d-428a-8680-f17d6ebdd185
caps.latest.revision: 3
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: 5d8c56be905d6dbfa966546c109a322e013baaac
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-chunk-serialized-data"></a>Guide pratique pour segmenter des données sérialisées

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Les deux problèmes qui se produisent lors de l'envoi de grands ensembles de données dans des messages de services web sont les suivants :  
  
1.  Un grand jeu de travail (mémoire) en raison d'une mise en mémoire tampon effectuée par le moteur de sérialisation.  
  
2.  Une consommation de bande passante importante due à une inflation de 33 % après un encodage Base64.  
  
 Pour résoudre ces problèmes, implémentez l'interface <xref:System.Xml.Serialization.IXmlSerializable> pour contrôler la sérialisation et la désérialisation. Plus précisément, implémentez les méthodes <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> et <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> pour segmenter les données.  
  
### <a name="to-implement-server-side-chunking"></a>Pour implémenter la segmentation côté serveur  
  
1.  Sur l'ordinateur serveur, la méthode Web doit désactiver la mise en mémoire tampon ASP.NET et retourner un type qui implémente <xref:System.Xml.Serialization.IXmlSerializable>.  
  
2.  Le type qui implémente <xref:System.Xml.Serialization.IXmlSerializable> segmente les données dans la méthode <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>.  
  
### <a name="to-implement-client-side-processing"></a>Pour implémenter le traitement côté client  
  
1.  Modifiez la méthode Web sur le proxy client pour retourner le type qui implémente <xref:System.Xml.Serialization.IXmlSerializable>. Vous pouvez utiliser un <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> pour effectuer cette opération automatiquement (non illustrée ici).  
  
2.  Implémentez la méthode <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> pour lire le flux de données segmenté et écrire les octets sur le disque. Cette implémentation déclenche également des événements de progression qui peuvent être utilisés par un contrôle graphique, tel qu'une barre de progression.  
  
## <a name="example"></a>Exemple  
L'exemple de code suivant illustre la méthode Web sur le client qui désactive la mise en mémoire tampon ASP.NET. Il affiche également l'implémentation côté client de l'interface <xref:System.Xml.Serialization.IXmlSerializable> qui segmente les données dans la méthode <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>.  
  
[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)] [!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)] [!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)] [!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
-   Le code utilise les espaces de noms suivants : <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization> et <xref:System.Xml.Schema>.  
  
## <a name="see-also"></a>Voir aussi  
 [Sérialisation personnalisée](custom-serialization.md)

