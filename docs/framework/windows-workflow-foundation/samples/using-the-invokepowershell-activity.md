---
title: "Utilisation de l&#39;activit&#233; InvokePowerShell | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 956251a0-31ca-4183-bf76-d277c08585df
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Utilisation de l&#39;activit&#233; InvokePowerShell
L'exemple InvokePowerShell montre comment appeler des commandes Windows PowerShell à l'aide de l'activité `InvokePowerShell`.  
  
## Démonstrations  
  
-   Innovation simple des commandes Windows PowerShell.  
  
-   Récupérer des valeurs du pipeline de sortie Windows PowerShell et les stocker dans des variables de workflow.  
  
-   Passer des données dans Windows PowerShell en tant que pipeline d'entrée pour une commande en cours d'exécution.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## Discussion  
 Cet exemple contient les trois projets suivants.  
  
|Nom du projet|Description|Fichiers principaux|  
|-------------------|-----------------|-------------------------|  
|CodedClient|Exemple d'application cliente qui utilise l'activité PowerShell.|-   **Program.cs** : crée par programmation un workflow basé sur une séquence qui appelle l'activité InvokePowerShell.|  
|DesignerClient|Ensemble d'activités personnalisées qui contiennent l'activité personnalisée `InvokePowerShell` et d'autres activités personnalisées diverses, et un workflow qui les utilise.|<ul><li>Activités :<br /><br /> <ul><li>**PrintCollection.cs** : activité d'assistance qui imprime tous les éléments d'une collection sur la console.</li><li>**ReadLine.cs** : activité d'assistance destinée à la lecture de l'entrée à partir de la console.</li></ul></li><li>Système de fichiers :<br /><br /> <ul><li>**Copy.xaml** : activité qui copie un fichier.</li><li>**CreateFile.xaml** : activité qui crée un fichier.</li><li>**DeleteFile.xaml** : activité qui supprime un fichier.</li><li>**MakeDir.xaml** : activité qui crée un répertoire.</li><li>**Move.xaml** : activité qui déplace un fichier.</li><li>**ReadFile.xaml** : activité que lit un fichier et retourne son contenu.</li><li>**TestPath.xaml** : activité qui teste l'existence d'un chemin d'accès.</li></ul></li><li>Processus :<br /><br /> <ul><li>**GetProcess.xaml** : activité qui obtient la liste des processus en cours d'exécution.</li><li>**StopProcess.xaml** : activité qui arrête un processus spécifique.</li></ul></li><li>**Program.cs** : appelle le workflow Sequence1.</li><li>**Sequence1.xaml** : workflow basé sur une séquence.</li></ul>|  
|PowerShell|Activité `InvokePowerShell` et les concepteurs qui lui sont associés.|Fichiers d'activité<br /><br /> -   **ExecutePowerShell.cs** : logique d'exécution principale de l'activité.<br />-   **InvokePowerShell.cs** : wrapper autour de la logique d'exécution principale, qui contient une version générique \(valeur de retour\) et une version non générique \(valeur autre que la valeur de retour\).Il s'agit de l'interface publique pour l'activité.<br />-   **NoPersistZone.cs** : cette activité empêche toutes activités enfants de devenir persistantes.Cette classe est utilisée dans l'implémentation de l'activité `InvokePowerShell` pour empêcher que l'activité soit rendue persistante au milieu de l'exécution.<br /><br /> Fichiers de concepteur :<br /><br /> 1.  **ArgumentDictionaryEditor.cs** : boîte de dialogue Windows qui permet à l'utilisateur de modifier les arguments de l'activité `InvokePowerShell`.<br />2.  **GenericInvokePowerShellDesigner.xaml** et **GenericInvokePowerShellDesigner.xaml.cs** : définit l'apparence de l'activité `InvokePowerShell` générique dans le [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].<br />3.  **InvokePowerShellDesigner.xaml** et **InvokePowerShellDesigner.cs** : définit l'apparence de l'activité `InvokePowerShell` non générique dans le [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].|  
  
 Les projets clients sont traités en premier, car il est plus facile de comprendre les fonctionnalités internes de l'activité PowerShell une fois que son utilisation est comprise.  
  
## Utilisation de cet exemple  
 Les sections suivantes expliquent comment utiliser les trois projets dans l'exemple.  
  
### Utilisation du projet client encodé  
 L'exemple de client crée par programmation une activité de séquence, laquelle contient des exemples de plusieurs méthodes différentes de l'utilisation de l'activité `InvokePowerShell`.Le premier appel lance le Bloc\-notes.  
  
```  
new InvokePowerShell()  
{  
    CommandText = "notepad"  
},  
  
```  
  
 Le deuxième appel obtient la liste des processus en cours d'exécution sur l'ordinateur local.  
  
```  
new InvokePowerShell<Process>()  
{  
    CommandText = "Get-Process",  
    Output = processes1,  
},  
  
```  
  
 `Output` est la variable utilisée pour stocker la sortie de la commande.  
  
 L'appel suivant montre comment exécuter une étape de post\-traitement sur chaque sortie individuelle de l'appel de PowerShell.`InitializationAction` a la valeur d'une fonction qui génère une représentation sous forme de chaîne pour chaque processus.La collection de ces chaînes est retournée dans la variable `Output` par l'activité `InvokePowerShell<string>`.  
  
 Les appels `InvokePowerShell` suivants montrent le passage de données dans l'activité et l'obtention des sorties et des erreurs.  
  
### Utilisation du projet DesignerClient  
 Le projet DesignerClient est composé d'un ensemble d'activités personnalisées, presque toutes étant générées de façon à contenir l'activité `InvokePowerShell`.La plupart des activités appellent la version non générique de l'activité `InvokePowerShell` et n'attendent pas de valeur de retour.D'autres activités utilisent la version générique de l'activité `InvokePowerShell` et utilisent l'argument `InitializationAction` pour post\-traiter les résultats.  
  
## Utilisation du projet PowerShell  
 L'action principale de l'activité se produit dans la classe `ExecutePowerShell`.Étant donné que l'exécution des commandes PowerShell ne doit pas bloquer le thread de workflow principal, l'activité est créée de façon à être une activité asynchrone en héritant de la classe <xref:System.Activities.AsyncCodeActivity>.  
  
 La méthode <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> est appelée par le runtime du workflow pour commencer l'exécution de l'activité.Il commence par appeler les API PowerShell pour créer un pipeline PowerShell.  
  
```  
runspace = RunspaceFactory.CreateRunspace();  
runspace.Open();  
pipeline = runspace.CreatePipeline();  
  
```  
  
 Il crée ensuite une commande PowerShell et la remplit avec des paramètres et des variables.  
  
```  
Command cmd = new Command(this.CommandText, this.IsScript);   
// loop over parameters and run: cmd.Parameters.Add(...)  
// loop over variables and run: runspace.SessionStateProxy.SetVariable(...)  
pipeline.Commands.Add(cmd);  
  
```  
  
 Les entrées redirigées sont également envoyées au pipeline à ce stade.Enfin, le pipeline est inclus dans un wrapper dans un objet `PipelineInvokerAsyncResult` et retourné.L'objet `PipelineInvokerAsyncResult` enregistre un écouteur et appelle le pipeline.  
  
```  
pipeline.InvokeAsync();  
  
```  
  
 Lorsque l'exécution se termine, la sortie et les erreurs sont stockées dans le même objet `PipelineInvokerAsyncResult`, et le contrôle est remis au runtime du workflow en appelant la méthode de rappel initialement passée à <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.  
  
 À la fin de l'exécution de la méthode, le runtime du workflow appelle la méthode <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> de l'activité.  
  
 La classe `InvokePowerShell` inclut dans un wrapper la classe `ExecutePowerShellCommand` et crée deux versions de l'activité : une version générique et une version non générique.La version non générique retourne directement la sortie de l'exécution de PowerShell, tandis que la version générique transforme les résultats individuels en type générique.  
  
 La version générique de l'activité est implémentée sous la forme d'un workflow séquentiel qui appelle `ExecutePowerShellCommand` et post\-traite ses résultats.Pour chaque élément de la collection des résultats, l'étape de post\-traitement appelle `InitializationAction` s'il est défini.Sinon, elle effectue un cast simple.  
  
```  
new ForEach<PSObject>  
{  
    Values = psObjects,  
    Body = new ActivityAction<PSObject>  
    {  
        Argument = psObject,  
        Handler = new Sequence  
        {  
            Activities =  
            {  
                new If  
                {  
                    Condition = // Is InitializationAction set?  
                    Then = new InvokeFunc<PSObject, TResult>  
                    {  
                        Argument = psObject,  
                        Result = outputObject,  
                        Func = this.InitializationAction  
                    },  
                    Else = new Assign<TResult>  
                    {  
                        To = outputObject,  
                        Value = new InArgument<TResult>(ctx => (TResult) psObject.Get(ctx).BaseObject),  
                    }  
                },  
                new AddToCollection<TResult>  
                {  
                    Collection = outputObjects,  
                    Item = outputObject  
                },  
            }  
        }  
    }  
},  
  
```  
  
 Un concepteur a été créé pour chacune des deux activités `InvokePowerShell` \(générique et non générique\).InvokePowerShellDesigner.xaml et son fichier .cs associé définissent l'apparence de la version non générique de l'activité `InvokePowerShell` dans le [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].À l'intérieur d'InvokePowerShellDesigner.xaml, un <xref:System.Windows.Controls.DockPanel> est utilisé pour représenter l'interface graphique.  
  
```  
<DockPanel x:Uid="DockPanel_1" LastChildFill="True">  
        <TextBlock x:Uid="TextBlock_1" Text="CommandText" />  
        <TextBox x:Uid="TextBox_1" Text="{Binding Path=ModelItem.CommandText, Mode=TwoWay}"  
                 TextWrapping="WrapWithOverflow"  AcceptsReturn="True" MinLines="4" MaxLines="4"  
                 Background="{x:Null}" Margin="3" />  
    </DockPanel>  
  
```  
  
 Notez que la propriété `Text` de la zone de texte est une liaison bidirectionnelle qui vérifie que la valeur de la propriété `CommandText` de l'activité est équivalente à la valeur entrée dans le concepteur.  
  
 GenericInvokePowerShellDesigner.xaml et son fichier .cs associé définissent l'interface graphique pour l'activité `InvokePowerShell` générique.Le concepteur est légèrement plus compliqué, car il permet aux utilisateurs de définir un `InitializationAction`.L'élément clé est l'utilisation de <xref:System.Activities.Presentation.WorkflowItemPresenter> pour permettre le glisser\-déplacer d'activités enfants sur l'aire du concepteur `InvokePowerShell`.  
  
```  
<sap:WorkflowItemPresenter x:Uid="sap:WorkflowItemPresenter_1" Margin="0,10,0,10"  
    HintText="Drop Activities Here"  
    AllowedItemType="{x:Type sa:Activity}"  
    Item="{Binding Path=ModelItem.InitializationAction.Handler, Mode=TwoWay}"  
    Grid.Row="1" Grid.Column="1" />  
  
```  
  
 La personnalisation du concepteur ne s'arrête pas aux fichiers .xaml qui définissent l'apparence de l'activité sur la zone de conception.Les boîtes de dialogue utilisées pour afficher les paramètres de l'activité peuvent également être personnalisées.Ces paramètres et les variables PowerShell affectent le comportement des commandes PowerShell.L'activité les expose sous la forme de types <xref:System.Collections.Generic.Dictionary%601>.ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml et PropertyEditorResources.cs définissent la boîte de dialogue qui vous permet de modifier ces types.  
  
## Pour configurer, générer et exécuter l'exemple  
 Vous devez installer Windows PowerShell pour exécuter cet exemple.Windows PowerShell peut être installé à partir de l'emplacement suivant : [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=150383).  
  
#### Pour exécuter le client encodé  
  
1.  Ouvrez PowerShell.sln à l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Cliquez avec le bouton droit sur la solution, puis générez\-la.  
  
3.  Cliquez avec le bouton droit sur le projet **CodedClient**, puis sélectionnez **Définir comme projet de démarrage**.  
  
4.  Appuyez sur CTRL\+F5 pour exécuter l'application.  
  
#### Pour exécuter le client du concepteur  
  
1.  Ouvrez PowerShell.sln à l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Cliquez avec le bouton droit sur la solution, puis générez\-la.  
  
3.  Cliquez avec le bouton droit sur le projet **DesignerClient**, puis sélectionnez **Définir comme projet de démarrage**.  
  
4.  Appuyez sur CTRL\+F5 pour exécuter l'application.  
  
## Problèmes connus  
  
1.  Si le référencement de l'assembly ou du projet de l'activité `InvokePowerShell` à partir d'un autre projet génère une erreur de build, vous devrez peut\-être ajouter manuellement l'élément `<SpecificVersion>True</SpecificVersion>` au fichier .csproj du nouveau projet sous la ligne qui référence `InvokePowerShell`.  
  
2.  Si Windows PowerShell n'est pas installé, le message d'erreur suivant s'affiche dans Visual Studio dès que vous ajoutez une activité `InvokePowerShell` sur un workflow : `Le Concepteur de Workflow a rencontré des problèmes avec votre document. Impossible de charger le fichier ou l'assembly 'System.Management.Automation' ou une de ses dépendances. Le système ne parvient pas à localiser le fichier spécifié.`  
  
3.  Dans Windows PowerShell 2.0, l'appel par programmation de `$input.MoveNext()` échoue et les scripts qui utilisent `$input.MoveNext()` produisent des erreurs et des résultats inattendus.Pour remédier à ce problème, envisagez d'utiliser le verbe PowerShell `foreach` au lieu d'appeler `MoveNext()` lors de l'itération au sein d'un tableau.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## Voir aussi