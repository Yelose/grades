<details><summary>Using Vue</summary>

# teacher-grades

This website is made with Vue 3

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

### Run Unit Tests with [Vitest](https://vitest.dev/)

```sh
npm run test:unit
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```

</details>

<details><summary>Exercise requirements</summary>
 
## Exercise to practice with Vue.

* Requirements:
  * Design an app that records student grades. 
  * The app should have two views as shown in the [figma layout](https://www.figma.com/file/AZLLzHiUAiPLiETDMCm7rk/Vue---Bolet%C3%ADn-de-notas). 
  * In the view where the qualifications should be listed, you have two possible options, choose the one you like best or start with the first and then try the second option.
  * Remember that the note must be numerical but in the qualifications they must be shown according to the scale.
  * Minimum 3 subjects.
  * Scale:
    * 0-3: Very poor
    * 3-5: Insufficient
    * 5-6: Enough
    * 6-7: Good
    * 7-9: notable
    * 9-10: Outstanding
 
 NOTE: Remember that if you think of something to improve it is always welcome.
 
</details>


<details><summary>User Flow</summary>
 
```mermaid
  
   graph LR

    subgraph VIEWS
        home(Home View)
        home-->goHome([go to app button])
        clickHome{click}
        goHome-->clickHome-->grades

        subgraph GRADES 
        grades(Grades View)
        store--show data--->grades
            subgraph FORM 
                formComponent(Form Component)
                formComponent-->name
                formComponent-->subject
                formComponent-->grade
                name[/Student Name input/]
                name-->exists
                exists[[exists?]]
                exists--no-->addNewStudent(Add new student)
                exists--yes-->allFilled
                subject[/Subject option input/]
                subject-->subjectSelected
                subjectSelected([Subject Selected?])
                subjectSelected--no--->msg2
                subjectSelected--yes-->allFilled
                msg2[Please select a subject]
                grade[/Grade input/]
                gradeFilled([filled as number 0-100?])
                grade-->gradeFilled
                gradeFilled--no-->msg1[please write a number from 0 to 100]
                gradeFilled--yes-->convertToString
                convertToString[\convert grade to A-F/]-->allFilled
                allFilled[all fields filled]
                allFilled--yes-->addToStore
            end  
            subgraph Store
                store[(Store)]
                store-->allFilled
                addToStore{add data}
                addToStore--to current student-->store
                addNewStudent-->store
            end  
        end        
    end            

  
```
  
</details>
