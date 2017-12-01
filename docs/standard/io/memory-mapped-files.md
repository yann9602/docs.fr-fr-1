---
title: "Fichiers mappés en mémoire"
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
helpviewer_keywords:
- memory-mapped files
- inter-process communiation
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
caps.latest.revision: "24"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2602d431aada7b3e0ee226eed319903492022ae9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="memory-mapped-files"></a>Fichiers mappés en mémoire
Un fichier mappé en mémoire comporte le contenu d'un fichier en mémoire virtuelle. Ce mappage entre un espace de fichier et de la mémoire permet à une application, y compris plusieurs processus modifier le fichier à lire et écrire directement dans la mémoire. En commençant par le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], vous pouvez utiliser du code managé pour accéder aux fichiers mappés en mémoire de la même façon que les fonctions Windows natives accéder aux fichiers mappés en mémoire, comme décrit dans [fichiers http://go.Microsoft.com/fwlink/?linkid=180801 dans Win32](http://go.microsoft.com/fwlink/?linkid=180801).  
  
 Il existe deux types de fichiers mappés en mémoire :  
  
-   Fichiers mappés en mémoire persistantes  
  
     Fichiers persistants sont des fichiers mappés en mémoire qui sont associés à un fichier source sur un disque. Lorsque le dernier processus a fini de travailler avec le fichier, les données sont enregistrées dans le fichier source sur le disque. Ces fichiers mappés en mémoire sont adaptés pour travailler avec les fichiers sources extrêmement volumineux.  
  
-   Fichiers mappés en mémoire non persistants  
  
     Fichiers non persistants sont des fichiers mappés en mémoire qui ne sont pas associés à un fichier sur un disque. Lorsque le dernier processus a fini de travailler avec le fichier, les données sont perdues et le fichier est récupéré par le garbage collection. Ces fichiers sont appropriés pour la création d’une mémoire partagée pour les communications entre processus (IPC).  
  
## <a name="processes-views-and-managing-memory"></a>Gestion de mémoire, des vues et des processus  
 Fichiers mappés en mémoire peuvent être partagés entre plusieurs processus. Processus peuvent être mappés dans le même fichier mappé en mémoire à l’aide d’un nom commun qui est attribué par le processus qui a créé le fichier.  
  
 Pour utiliser un fichier mappé en mémoire, vous devez créer une vue de l’intégralité du fichier mappé en mémoire ou une partie de celui-ci. Vous pouvez également créer plusieurs vues à la même partie du fichier mappé en mémoire, en créant la mémoire simultanés. Pour les deux vues restent simultanées, elles doivent être créées à partir du même fichier mappé en mémoire.  
  
 Plusieurs vues peuvent également être nécessaires si le fichier est supérieur à la taille de l’espace de mémoire logique de l’application disponible pour le mappage (2 Go sur un ordinateur 32 bits) de mémoire.  
  
 Il existe deux types de vues : vue de l’accès et le mode d’accès aléatoire de flux. Utilisez les vues d’accès continu pour un accès séquentiel à un fichier ; Cela est recommandé pour les fichiers non persistants et IPC. Vues d’accès aléatoire sont privilégiés pour l’utilisation des fichiers persistants.  
  
 Fichiers mappés en mémoire sont accessibles via le Gestionnaire de mémoire du système d’exploitation, le fichier est donc automatiquement partitionné en un nombre de pages et accessibles en fonction des besoins. Vous n’avez pas à gérer la mémoire vous-même.  
  
 L’illustration suivante montre comment plusieurs processus peuvent avoir plusieurs et qui se chevauchent vues dans le même fichier mappé en mémoire en même temps.  
  
 ![Affiche les vues à une mémoire &#45; le fichier mappé. ] (../../../docs/standard/io/media/memmappersisted.png "MemMapPersisted")  
Plusieurs et avec chevauchement des vues dans un fichier mappé en mémoire  
  
## <a name="programming-with-memory-mapped-files"></a>Programmation avec les fichiers mappés en mémoire  
 Le tableau suivant fournit un guide pour l’utilisation des objets de fichier mappé en mémoire et leurs membres.  
  
|Tâche|Méthodes ou propriétés à utiliser|  
|----------|----------------------------------|  
|Pour obtenir un <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objet qui représente un fichier mappé en mémoire persistant à partir d’un fichier sur disque.|Méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>.|  
|Pour obtenir un <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objet qui représente un fichier mappé en mémoire non persistant (non associé à un fichier sur disque).|Méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>.<br /><br /> ou<br /><br /> Méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>.|  
|Pour obtenir un <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> l’objet d’un fichier mappé en mémoire existant (persistant ou non persistant).|Méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType>.|  
|Pour obtenir un <xref:System.IO.UnmanagedMemoryStream> objet pour un accès séquentiel affichage au fichier mappé en mémoire.|Méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType>.|  
|Pour obtenir un <xref:System.IO.UnmanagedMemoryAccessor> de l’objet pour une vue d’un accès aléatoire à un mappé en mémoire fichier.|Méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType>.|  
|Pour obtenir un <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> objet à utiliser avec le code non managé.|Propriété <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>.<br /><br /> ou<br /><br /> Propriété <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>.<br /><br /> ou<br /><br /> Propriété <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>.|  
|Pour différer l’allocation de mémoire tant que la vue est créée (fichiers non persistants uniquement).<br /><br /> (Pour déterminer la taille de page en cours du système, utilisez le <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> propriété.)|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A>méthode avec le <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> valeur.<br /><br /> ou<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A>les méthodes qui ont un <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> énumération en tant que paramètre.|  
  
### <a name="security"></a>Sécurité  
 Vous pouvez appliquer des droits d’accès lorsque vous créez un fichier mappé en mémoire, en utilisant les méthodes suivantes qui prennent un <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> énumération en tant que paramètre :  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 Vous pouvez spécifier les droits d’accès pour l’ouverture d’un fichier mappé en mémoire à l’aide de la <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> méthodes qui prennent un <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> en tant que paramètre.  
  
 En outre, vous pouvez inclure un <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> objet qui contient des règles d’accès prédéfinies.  
  
 Pour appliquer des règles d’accès nouvelles ou modifiées dans un fichier mappé en mémoire, utilisez le <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> (méthode). Pour récupérer l’accès ou d’audit à partir d’un fichier existant, utilisez la <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> (méthode).  
  
## <a name="examples"></a>Exemples  
  
### <a name="persisted-memory-mapped-files"></a>Fichiers mappés en mémoire persistantes  
 Le <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> méthodes créent un fichier mappé en mémoire à partir d’un fichier existant sur le disque.  
  
 L’exemple suivant crée une vue mappé en mémoire d’une partie d’un fichier très volumineux et manipule une partie de celui-ci.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 L’exemple suivant ouvre le même fichier mappé en mémoire pour un autre processus.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a>Fichiers mappés en mémoire non persistants  
 Le <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> et <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> méthodes créent un fichier mappé en mémoire qui n’est pas mappé à un fichier existant sur le disque.  
  
 L’exemple suivant se compose de trois processus distincts (applications console) qui écrivent des valeurs booléennes dans un fichier mappé en mémoire. La séquence suivante d’actions se produisent :  
  
1.  `Process A`crée le fichier mappé en mémoire et écrit une valeur.  
  
2.  `Process B`Ouvre le fichier mappé en mémoire et écrit une valeur.  
  
3.  `Process C`Ouvre le fichier mappé en mémoire et écrit une valeur.  
  
4.  `Process A`lit et affiche les valeurs à partir du fichier mappé en mémoire.  
  
5.  Après avoir `Process A` est terminé avec le fichier mappé en mémoire, le fichier est immédiatement libéré par le garbage collection.  
  
 Pour exécuter cet exemple, procédez comme suit :  
  
1.  Compilez les applications et ouvrez trois fenêtres d’invite de commandes.  
  
2.  Dans la première fenêtre d’invite de commandes, exécutez `Process A`.  
  
3.  Dans la deuxième fenêtre d’invite de commandes, exécutez `Process B`.  
  
4.  Retour à `Process A` et appuyez sur ENTRÉE.  
  
5.  Dans la troisième fenêtre d’invite de commandes, exécutez `Process C`.  
  
6.  Retour à `Process A` et appuyez sur ENTRÉE.  
  
 La sortie de `Process A` est comme suit :  
  
```  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 **Processus A**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 **Processus B**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 **Processus C**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier et flux de données E/S](../../../docs/standard/io/index.md)
