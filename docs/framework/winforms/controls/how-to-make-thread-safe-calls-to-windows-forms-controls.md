---
title: "Comment&#160;: faire des appels thread-safe aux contr&#244;les Windows&#160;Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHInvalidOperation.WinForms.IllegalCrossThreadCall"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "sécurité des threads, appel de contrôles (Windows Forms)"
  - "appel de contrôles, sécurité des threads (Windows Forms)"
  - "CheckForIllegalCrossThreadCalls (propriété Windows Forms)"
  - "contrôles Windows Forms, multithreading"
  - "BackgroundWorker (classe), exemples"
  - "threads (Windows Forms), appels inter-threads"
  - "contrôles (Windows Forms), multithreading"
ms.assetid: 138f38b6-1099-4fd5-910c-390b41cbad35
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Comment&#160;: faire des appels thread-safe aux contr&#244;les Windows&#160;Forms
Si vous utilisez le multithreading pour améliorer les performances de vos applications Windows Forms, vous devez vous assurer que les appels à vos contrôles sont thread\-safe.  
  
 L'accès aux contrôles Windows Forms n'est pas fondamentalement thread\-safe. Si plusieurs threads manipulent l'état d'un contrôle, il est possible de forcer ce contrôle dans un état incohérent. D'autres bogues liés aux threads sont possibles, tels que des blocages et des conditions de concurrence critique. Il est important de s'assurer que l'accès à vos contrôles est thread\-safe.  
  
 Il est risqué d'appeler un contrôle à partir d'un thread autre que celui qui a créé le contrôle sans utiliser la méthode <xref:System.Windows.Forms.Control.Invoke%2A>. Voici un exemple d'appel qui n'est pas thread\-safe.  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#6)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#6)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#6)]  
  
 Le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] vous aide à savoir quand vous accédez à vos contrôles d'une manière non thread\-safe. Quand vous exécutez votre application dans le débogueur et qu'un autre thread que celui qui a créé un contrôle tente d'appeler ce dernier, le débogueur lève une exception <xref:System.InvalidOperationException> avec le message "Le contrôle *nom du contrôle* a fait l'objet d'un accès à partir d'un thread autre que celui sur lequel il a été créé".  
  
 Cette exception est levée pendant le débogage et, dans certaines circonstances, au moment de l'exécution. Cette exception peut être levée quand vous déboguez des applications que vous avez écrites avec une version du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] antérieure au [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Il est fortement recommandé de résoudre ce problème quand vous le rencontrez. Toutefois, vous pouvez l'éviter en attribuant à la méthode <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A> la valeur `false`. Votre contrôle s'exécutera comme sous Visual Studio .NET 2003 et sous le [!INCLUDE[net_v11_short](../../../../includes/net-v11-short-md.md)].  
  
> [!NOTE]
>  Si vous utilisez des contrôles ActiveX sur un formulaire, vous pouvez recevoir l'exception inter\-threads <xref:System.InvalidOperationException> lors de l'exécution sous le débogueur. Quand cela se produit, le contrôle ActiveX ne prend pas en charge le multithreading. Pour plus d’informations sur l’utilisation des contrôles ActiveX avec Windows Forms, consultez [Applications Windows Forms et non managées](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md). Si vous utilisez Visual Studio, vous pouvez éviter cette exception en désactivant le processus d’hébergement de Visual Studio. Pour plus d’informations, consultez [Comment : désactiver le processus d'hébergement](../Topic/How%20to:%20Disable%20the%20Hosting%20Process.md).  
  
## Appels thread\-safe aux contrôles Windows Forms  
  
#### Pour effectuer un appel thread\-safe à un contrôle Windows Forms  
  
1.  Interrogez la propriété <xref:System.Windows.Forms.Control.InvokeRequired%2A> du contrôle.  
  
2.  Si <xref:System.Windows.Forms.Control.InvokeRequired%2A> renvoie `true`, appelez <xref:System.Windows.Forms.Control.Invoke%2A> avec un délégué qui appelle le contrôle.  
  
3.  Si <xref:System.Windows.Forms.Control.InvokeRequired%2A> renvoie `false`, appelez le contrôle directement.  
  
 Dans l'exemple de code suivant, un appel thread\-safe est implémenté dans la méthode `ThreadProcSafe`, qui est exécutée par le thread d'arrière\-plan. Si le <xref:System.Windows.Forms.TextBox> du contrôle <xref:System.Windows.Forms.Control.InvokeRequired%2A> renvoie `true`, la méthode `ThreadProcSafe` crée une instance de `SetTextCallback` et la passe à la méthode <xref:System.Windows.Forms.Control.Invoke%2A> du formulaire. Dans ce cas, la méthode `SetText` est appelée sur le thread qui a créé le contrôle <xref:System.Windows.Forms.TextBox>, et dans ce contexte de thread, la propriété <xref:System.Windows.Forms.Control.Text%2A> est définie directement.  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#7)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#7)]  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#3)]  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#8](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#8)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#8)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#8)]  
  
## Appels thread\-safe à l'aide de BackgroundWorker  
 Le meilleur moyen d'implémenter le multithreading dans votre application est d'utiliser le composant <xref:System.ComponentModel.BackgroundWorker>. Le composant <xref:System.ComponentModel.BackgroundWorker> utilise un modèle basé sur les événements pour le multithreading. Le thread d'arrière\-plan exécute le gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.DoWork>, et le thread qui crée vos contrôles exécute les gestionnaires d'événements <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> et <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>. Vous pouvez appeler vos contrôles depuis les gestionnaires d'événements <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> et <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>.  
  
#### Pour effectuer des appels thread\-safe à l'aide de BackgroundWorker  
  
1.  Créez une méthode pour effectuer le travail dans le thread d'arrière\-plan. N'appelez pas les contrôles créés par le thread principal dans cette méthode.  
  
2.  Créez une méthode pour signaler les résultats de votre travail d'arrière\-plan une fois celui\-ci terminé. Vous pouvez appeler les contrôles créés par le thread principal dans cette méthode.  
  
3.  Liez la méthode créée à l'étape 1 à l'événement <xref:System.ComponentModel.BackgroundWorker.DoWork> d'une instance de <xref:System.ComponentModel.BackgroundWorker> et liez la méthode créée à l'étape 2 à l'événement <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> de la même instance.  
  
4.  Pour démarrer le thread d'arrière\-plan, appelez la méthode <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> de l'instance <xref:System.ComponentModel.BackgroundWorker>.  
  
 Dans l'exemple de code suivant, le gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.DoWork> utilise <xref:System.Threading.Thread.Sleep%2A> pour simuler un travail qui prend du temps. Il n'appelle pas le contrôle <xref:System.Windows.Forms.TextBox> du formulaire. La propriété <xref:System.Windows.Forms.TextBox> du contrôle <xref:System.Windows.Forms.Control.Text%2A> est directement définie dans le gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>.  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#5)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#5)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#5)]  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#9](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#9)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#9)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#9)]  
  
 Vous pouvez également signaler la progression d'une tâche en arrière\-plan à l'aide de l'événement <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>. Pour obtenir un exemple qui intègre cet événement, consultez <xref:System.ComponentModel.BackgroundWorker>.  
  
## Exemple  
 L'exemple de code suivant est une application Windows Forms complète constituée d'un formulaire avec trois boutons et une zone de texte. Le premier bouton montre un accès inter\-threads non sécurisé, le deuxième bouton montre l'accès sécurisé à l'aide de <xref:System.Windows.Forms.Control.Invoke%2A>, et le troisième bouton montre l'accès sécurisé à l'aide de <xref:System.ComponentModel.BackgroundWorker>.  
  
> [!NOTE]
>  Pour obtenir des instructions expliquant comment exécuter cet exemple, consultez [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/fr-fr/cc447f7e-4c3b-4397-9d05-aeba3ca49416). Cet exemple nécessite des références aux assemblys System.Drawing et System.Windows.Forms.  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#1)]  
  
 Quand vous exécutez l'application et cliquez sur le bouton **Unsafe Call**, vous voyez immédiatement "Written by the main thread" \(Écrit par le thread principal\) dans la zone de texte. Deux secondes plus tard, quand l'appel non sécurisé est tenté, le débogueur Visual Studio indique qu'une exception a été levée. Le débogueur s'arrête au niveau de la ligne du thread d'arrière\-plan qui a tenté d'écrire directement dans la zone de texte. Vous devez redémarrer l'application pour tester les deux autres boutons. Quand vous cliquez sur le bouton **Safe Call**, la mention "Written by the main thread" s'affiche dans la zone de texte. Deux secondes plus tard, la zone de texte est définie sur "Written by the main thread \(Invoke\)", ce qui indique que la méthode <xref:System.Windows.Forms.Control.Invoke%2A> a été appelée. Quand vous cliquez sur le bouton **Safe BW Call**, la mention "Written by the main thread" s'affiche dans la zone de texte. Deux secondes plus tard, la zone de texte est définie sur "Written by the main thread after the background thread completed" \(Écrit par le thread principal à la fin du thread d'arrière\-plan\), ce qui indique que le gestionnaire de l'événement <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> de <xref:System.ComponentModel.BackgroundWorker> a été appelé.  
  
## Programmation fiable  
  
> [!CAUTION]
>  Quand vous utilisez un type quelconque de multithreading, vous vous exposez potentiellement à des bogues importants et complexes. Pour plus d’informations, consultez [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) avant d’implémenter une solution utilisant le multithreading.  
  
## Voir aussi  
 <xref:System.ComponentModel.BackgroundWorker>   
 [Comment : exécuter une opération en arrière\-plan](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)   
 [Comment : implémenter un formulaire qui utilise une opération d'arrière\-plan](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)   
 [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [Applications Windows Forms et non managées](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)