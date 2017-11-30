---
title: "Paramètres et valeurs de retour pour les procédures multithread (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 071e0aa916e4b3464c7c0cbff6596cabc6b67906
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a>Paramètres et valeurs de retour pour les procédures multithread (Visual Basic)
Fournir des paramètres et retourner des valeurs dans une application multithread est complexe, car le constructeur de la classe thread doit recevoir une référence à une procédure qui n’accepte aucun argument et ne retourne aucune valeur. Les sections suivantes présentent plusieurs moyens simples pour fournir des paramètres et retourner des valeurs à partir de procédures exécutées sur des threads distincts.  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>Fournir des paramètres pour des procédures multithread  
 Le meilleur moyen de fournir des paramètres pour un appel de méthode multithread consiste à inclure la méthode cible dans une classe et à définir les champs de cette classe à utiliser comme paramètres pour le nouveau thread. Cette approche présente l’avantage de vous permettre de créer une autre instance de la classe, avec ses propres paramètres, chaque fois que vous souhaitez démarrer un nouveau thread. Prenons l’exemple d’une fonction calculant la surface d’un triangle, comme dans le code suivant :  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 Vous pouvez écrire une classe qui inclut la fonction `CalcArea` et crée des champs pour stocker les paramètres d’entrée, comme suit :  
  
```vb  
Class AreaClass  
    Public Base As Double  
    Public Height As Double  
    Public Area As Double  
    Sub CalcArea()  
        Area = 0.5 * Base * Height  
        MessageBox.Show("The area is: " & Area.ToString)  
    End Sub  
End Class  
```  
  
 Pour utiliser `AreaClass`, vous créez un objet `AreaClass`, puis vous définissez les propriétés `Base` et `Height` comme indiqué dans le code suivant :  
  
```vb  
Protected Sub TestArea()  
    Dim AreaObject As New AreaClass  
    Dim Thread As New System.Threading.Thread(  
                        AddressOf AreaObject.CalcArea)  
    AreaObject.Base = 30  
    AreaObject.Height = 40  
    Thread.Start()  
End Sub  
```  
  
 Notez que la procédure `TestArea` ne vérifie pas la valeur du champ `Area` après avoir appelé la méthode `CalcArea`. Étant donné que `CalcArea` s’exécute sur un thread distinct, le champ `Area` risque de ne pas être défini si vous le vérifiez immédiatement après avoir appelé `Thread.Start`. La section suivante présente une méthode plus appropriée pour retourner des valeurs à partir de procédures multithread.  
  
## <a name="returning-values-from-multithreaded-procedures"></a>Retourner des valeurs à partir de procédures multithread  
 Retourner des valeurs à partir de procédures exécutées sur des threads distincts est compliqué du fait que les procédures ne peuvent pas être des fonctions, ni utiliser d’arguments `ByRef`. Le moyen le plus simple de retourner des valeurs consiste à utiliser le composant <xref:System.ComponentModel.BackgroundWorker> pour gérer vos threads et déclencher un événement à la fin de la tâche, puis traiter les résultats à l’aide d’un gestionnaire d’événements.  
  
 L’exemple suivant retourne une valeur en déclenchant un événement à partir d’une procédure exécutée sur un thread distinct :  
  
```vb  
Private Class AreaClass2  
    Public Base As Double  
    Public Height As Double  
    Function CalcArea() As Double  
        ' Calculate the area of a triangle.  
        Return 0.5 * Base * Height  
    End Function  
End Class  
  
Private WithEvents BackgroundWorker1 As New System.ComponentModel.BackgroundWorker  
  
Private Sub TestArea2()  
    Dim AreaObject2 As New AreaClass2  
    AreaObject2.Base = 30  
    AreaObject2.Height = 40  
  
    ' Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2)  
End Sub  
  
' This method runs on the background thread when it starts.  
Private Sub BackgroundWorker1_DoWork(  
    ByVal sender As Object,   
    ByVal e As System.ComponentModel.DoWorkEventArgs  
    ) Handles BackgroundWorker1.DoWork  
  
    Dim AreaObject2 As AreaClass2 = CType(e.Argument, AreaClass2)  
    ' Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea()  
End Sub  
  
' This method runs on the main thread when the background thread finishes.  
Private Sub BackgroundWorker1_RunWorkerCompleted(  
    ByVal sender As Object,  
    ByVal e As System.ComponentModel.RunWorkerCompletedEventArgs  
    ) Handles BackgroundWorker1.RunWorkerCompleted  
  
    ' Access the result through the Result property.  
    Dim Area As Double = CDbl(e.Result)  
    MessageBox.Show("The area is: " & Area.ToString)  
End Sub  
```  
  
 Vous pouvez fournir des paramètres et retourner des valeurs aux threads de Thread Pool en utilisant la variable d’objet d’état `ByVal` facultative de la méthode <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>. Les threads de Timer Thread prennent également en charge un objet d’état à cet effet. Pour plus d’informations sur le regroupement de threads et les composants Timer thread, consultez [le regroupement de threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[le regroupement de threads](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) et [minuteries de threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : multithreading avec le composant BackgroundWorker (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [Regroupement des threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [Synchronisation des threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)  
 [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Applications multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Délégués](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Multithreading dans les composants](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
