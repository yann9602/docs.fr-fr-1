---
title: "Fichiers mapp&#233;s en m&#233;moire | Microsoft Docs"
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
  - "communication entre processus"
  - "fichiers mappés en mémoire"
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
caps.latest.revision: 24
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 24
---
# Fichiers mapp&#233;s en m&#233;moire
Un fichier mappé en mémoire comporte le contenu d'un fichier en mémoire virtuelle.  Ce mappage entre un fichier et un espace mémoire permet à une application, y compris les processus multiples, de modifier le fichier en lisant et en écrivant directement dans la mémoire.  Depuis [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], il est possible d'utiliser du code managé pour accéder aux fichiers mappés en mémoire de la même façon que les fonctions Windows natives accèdent aux fichiers mappés en mémoire, comme décrit dans [Gestion des fichiers mappés en mémoire dans Win32 \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?linkid=180801) dans MSDN Library.  
  
 Il existe deux types de fichiers mappés en mémoire :  
  
-   Fichiers mappés en mémoire persistants  
  
     Les fichiers persistants sont des fichiers mappés en mémoire associés à un fichier source sur un disque.  Lorsque le dernier processus a terminé d'utiliser le fichier, les données sont enregistrées dans le fichier source sur le disque.  Ces fichiers mappés en mémoire conviennent à l'utilisation de fichiers sources extrêmement volumineux.  
  
-   Fichiers mappés en mémoire non persistants  
  
     Les fichiers non persistants sont des fichiers mappés en mémoire qui ne sont pas associés à un fichier source sur un disque.  Lorsque le dernier processus a terminé d'utiliser le fichier, les données sont perdues et le fichier est récupéré par l'opération de nettoyage de la mémoire.  Ces fichiers conviennent à la création d'une mémoire partagée pour des communications entre processus.  
  
## Processus, vues, et gestion de mémoire  
 Les fichiers mappés en mémoire peuvent être partagés entre plusieurs processus.  Les processus peuvent être mappés vers le même fichier mappé en mémoire à l'aide d'un nom commun assigné par le processus qui a créé le fichier.  
  
 Pour utiliser un fichier mappé en mémoire, vous devez créer une vue du fichier dans son entier ou partiel.  Vous pouvez également créer plusieurs vues pour une même partie du fichier mappé en mémoire, ce qui crée une mémoire à accès concurrentiel.  Pour que deux vues restent simultanées, elles doivent être créées à partir du même fichier mappé en mémoire.  
  
 Il peut également être nécessaire d'utiliser plusieurs vues si la taille du fichier est supérieure à la taille de l'espace mémoire logique de l'application disponible pour le mappage de mémoire \(2 Go sur un ordinateur 32 bits\).  
  
 Il existe deux types de vues : la vue d'accès continu et la vue d'accès aléatoire.  Utilisez les vues d'accès continu pour un accès séquentiel à un fichier ; cette vue est recommandée pour les fichiers non persistants et les communications entre processus.  Les vues d'accès aléatoire sont préférées pour l'utilisation de fichiers persistants.  
  
 Les fichiers mappés en mémoire sont accessibles via le gestionnaire de mémoire du système d'exploitation pour que le fichier soit partitionné automatiquement en plusieurs pages et accessible autant que nécessaire.  Vous n'avez pas à gérer la mémoire vous\-même.  
  
 L'illustration suivante montre comment plusieurs processus peuvent avoir conjointement des vues multiples et superposées du même fichier mappé en mémoire.  
  
 ![Affiche les vues dans un fichier mappé en mémoire.](../../../docs/standard/io/media/memmappersisted.png "MemMapPersisted")  
Vues multiples et superposées d'un fichier mappé en mémoire  
  
## Programmation avec les fichiers mappés en mémoire  
 Le tableau suivant indique comment utiliser les objets de fichiers mappés en mémoire et leurs membres.  
  
|Tâche|Méthodes ou propriétés à utiliser|  
|-----------|---------------------------------------|  
|Pour obtenir un objet <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> qui représente le fichier mappé en mémoire persistant d'un fichier présent sur le disque.|Méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=fullName>.|  
|Pour obtenir un objet <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> qui représente un fichier mappé en mémoire non persistant \(non associé à un fichier sur le disque\).|Méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=fullName>.<br /><br /> \- ou \-<br /><br /> Méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=fullName>.|  
|Pour obtenir un objet <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> d'un fichier mappé en mémoire existant \(persistant ou non persistant\).|Méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=fullName>.|  
|Pour obtenir un objet <xref:System.IO.UnmanagedMemoryStream> pour une vue d'accès séquentiel du fichier mappé en mémoire.|Méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=fullName>.|  
|Pour obtenir un objet <xref:System.IO.UnmanagedMemoryAccessor> pour une vue d'accès aléatoire d'un fichier mappé en mémoire.|Méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=fullName>.|  
|Pour obtenir un objet <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> à utiliser avec du code non managé.|Propriété <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=fullName>.<br /><br /> \- ou \-<br /><br /> Propriété <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=fullName>.<br /><br /> \- ou \-<br /><br /> Propriété <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=fullName>.|  
|Pour différer l'allocation de mémoire tant que la vue n'est pas créée \(fichiers non persistants uniquement\).<br /><br /> \(Pour déterminer la taille de la mémoire de pagination du système actuel, utilisez la propriété <xref:System.Environment.SystemPageSize%2A?displayProperty=fullName>.\)|Méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> avec la valeur <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions?displayProperty=fullName>.<br /><br /> \- ou \-<br /><br /> Méthodes <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> qui ont une énumération <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> comme paramètre.|  
  
### Sécurité  
 Vous pouvez appliquer des droits d'accès lorsque vous créez un fichier mappé en mémoire, à l'aide des méthodes suivantes qui prennent une énumération <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> comme paramètre :  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=fullName>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=fullName>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=fullName>  
  
 Vous pouvez spécifier des droits d'accès pour l'ouverture d'un fichier mappé en mémoire existant à l'aide des méthodes <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> qui prennent un <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> comme paramètre.  
  
 De plus, vous pouvez inclure un objet <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> qui contient des règles d'accès prédéfinies.  
  
 Pour appliquer des règles d'accès nouvelles ou modifiées à un fichier mappé en mémoire, utilisez la méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A>.  Pour récupérer les règles d'accès ou d'audit d'un fichier existant, utilisez la méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A>.  
  
## Exemples  
  
### Fichiers mappés en mémoire persistants  
 Les méthodes <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> créent un fichier mappé en mémoire à partir d'un fichier existant stocké sur le disque.  
  
 L'exemple suivant crée une vue mappée en mémoire d'une partie d'un fichier extrêmement volumineux et en manipule une partie.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 L'exemple suivant ouvre le même fichier mappé en mémoire pour un autre processus.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### Fichiers mappés en mémoire non persistants  
 Les méthodes <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> et <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> créent un fichier mappé en mémoire qui n'est pas mappé à un fichier existant sur le disque.  
  
 L'exemple suivant est composé de trois processus distincts \(applications console\) qui écrivent des valeurs booléennes dans un fichier mappé en mémoire.  La séquence d'actions suivante se produit :  
  
1.  Le `Process A` crée le fichier mappé en mémoire et écrit une valeur dedans.  
  
2.  Le `Process B` ouvre le fichier mappé en mémoire et écrit une valeur dedans.  
  
3.  Le `Process C` ouvre le fichier mappé en mémoire et écrit une valeur dedans.  
  
4.  Le `Process A` lit et affiche les valeurs du fichier mappé en mémoire.  
  
5.  Une fois le `Process A` terminé avec le fichier mappé en mémoire, le fichier est immédiatement libéré par le garbage collection.  
  
 Pour exécuter cet exemple, procédez comme suit :  
  
1.  Compilez les applications et ouvrez trois fenêtres d'invite de commandes.  
  
2.  Dans la première fenêtre d'invite de commandes, exécutez le `Process A`.  
  
3.  Dans la deuxième fenêtre d'invite de commandes, exécutez le `Process B`.  
  
4.  Retournez au `Process A` et appuyez sur ENTRÉE.  
  
5.  Dans la troisième fenêtre d'invite de commandes, exécutez le `Process C`.  
  
6.  Retournez au `Process A` et appuyez sur ENTRÉE.  
  
 La sortie du `Process A` est la suivante :  
  
```  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 **Processus A**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 **Processus B**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 **Processus C**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## Voir aussi  
 [Fichier et flux de données E\/S](../../../docs/standard/io/index.md)