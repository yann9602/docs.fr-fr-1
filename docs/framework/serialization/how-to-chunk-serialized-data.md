---
title: "Comment&#160;: segmenter des donn&#233;es s&#233;rialis&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "sérialisation binaire, segmenter des données"
  - "sérialisation binaire, exemples"
  - "segmenter des données sérialisées"
  - "segmenter des données"
  - "segmenter de grands ensembles de données"
  - "sérialisation, segmenter des données"
  - "sérialisation, exemples"
ms.assetid: 22f1b818-7e0d-428a-8680-f17d6ebdd185
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Comment&#160;: segmenter des donn&#233;es s&#233;rialis&#233;es
Les deux problèmes qui se produisent lors de l'envoi de groupes de données volumineux dans des messages de services Web sont les suivants :  
  
1.  Un grand jeu de travail \(mémoire\) en raison d'une mise en mémoire tampon effectuée par le moteur de sérialisation.  
  
2.  Une consommation de bande passante importante due à une inflation de 33 % après un codage Base64.  
  
 Pour résoudre ces problèmes, implémentez l'interface <xref:System.Xml.Serialization.IXmlSerializable> pour contrôler la sérialisation et la désérialisation.Plus précisément, implémentez les méthodes <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> et <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> pour segmenter les données.  
  
### Pour implémenter la segmentation côté serveur  
  
1.  Sur l'ordinateur serveur, la méthode Web doit désactiver la mise en mémoire tampon ASP.NET et retourner un type qui implémente <xref:System.Xml.Serialization.IXmlSerializable>.  
  
2.  Le type qui implémente <xref:System.Xml.Serialization.IXmlSerializable> segmente les données dans la méthode <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>.  
  
### Pour implémenter le traitement côté client  
  
1.  Modifiez la méthode Web sur le proxy client pour retourner le type qui implémente <xref:System.Xml.Serialization.IXmlSerializable>.Vous pouvez utiliser un <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> pour effectuer cette opération automatiquement \(non illustrée ici\).  
  
2.  Implémentez la méthode <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> pour lire le flux de données segmenté et écrire les octets sur le disque.Cette implémentation déclenche également des événements de progression qui peuvent être utilisés par un contrôle graphique, tel qu'une barre de progression.  
  
## Exemple  
 L'exemple de code suivant illustre la méthode Web sur le client qui désactive la mise en mémoire tampon ASP.NET.Il affiche également l'implémentation côté client de l'interface <xref:System.Xml.Serialization.IXmlSerializable> qui segmente les données dans la méthode <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>.  
  
 [!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)]
 [!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)]
[!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)]
[!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## Compilation du code  
  
-   Le code utilise les espaces de noms suivants : <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization> et <xref:System.Xml.Schema>.  
  
## Voir aussi  
 [Sérialisation personnalisée](../../../docs/framework/serialization/custom-serialization.md)