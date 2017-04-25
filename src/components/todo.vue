<template>
    <div class="todo">
        <h1 class="title">Checklist</h1>
        <ui-tabs fullwidth="true" type="text">
            <ui-tab class="tabHeight addScroll" title="pending" >


                <ul class="tasks" >
                    <!--<list-of-tasks></list-of-tasks>-->
                    <transition-group  name="list" tag="li">
                        <li v-for="task in tasks" v-if="task.complete ? false : true" :class="{complete : task.complete}">
                            <ui-checkbox v-model="task.complete" :label="task.name"/>
                    </li>
                    </transition-group>
                </ul>


            </ui-tab>
            <ui-tab class="tabHeight addScroll" title="complete" >
                <ul class="tasks">

                    <li v-for="task in tasks" v-if="task.complete ? true : false" :class="{complete : task.complete}">
                        <transition name="list">
                        <ui-checkbox v-model="task.complete" :label="task.name"/>
                        </transition>
                    </li>

                </ul>

            </ui-tab>
        </ui-tabs>
        <div class="input_row">
            <ui-textbox class='width_input' placeholder="e.g. 'read vue.js guide'" v-model="newTaskName"
                        @keydown-enter="addTask"></ui-textbox>
            <ui-button color="primary" @click="addTask" icon="add" :disabled= "(newTaskName=='')? true : false" >Add</ui-button>
        </div>
    </div>
</template>

<script>
    export default {
        data () {
            return {
                newTaskName: '',
                tasks: [
                    {name: 'create skeleton of todo', complete: true},
                    {name: 'add ability to add tasks', complete: true},
                    {name: 'clear task name after clicking "Add"', complete: false},
                    {name: 'put "Add" button in one line with input', complete: false},
                    {name: 'add new task by hitting Enter instead of clicking "Add"', complete: false},
                    {name: 'replace <input> with <ui-checkbox> in tasks list', complete: false},
                    {name: 'when task is complete cross it out', complete: false},
                    {
                        name: 'split tasks into "pending" and "complete" tabs using keen-ui component <ui-tabs>',
                        complete: false
                    },
                    {name: 'don\'t allow to add empty tasks', complete: false},
                    {name: 'make list of tasks scrollable, if there\'re are a lot of tasks', complete: false},
                    {name: 'extract list item into a separate vue.js component', complete: false},
                    {name: 'persist tasks list in a local storage', complete: false},
                    {name: 'add animation on task completion', complete: false},
                ]
            }
        },

        methods: {
            replaceItem(){
                setTimeout(function () {
                    return false;
                }, 1000)
            },
            addTask () {
                this.tasks.push({name: this.newTaskName, complete: false});
                this.newTaskName = "";
            }
        }
    };
</script>

<style scoped lang="scss">
    .list-move{
        transition: transform 1s;
    }
    /*.list-leave-to{
        opacity: 1;
    }
    .list-leave{
        opacity: 0;
    }
    .list-enter-active{
        transition: all .3s ease
    }
    .list-enter{
        opacity: 0;
    }
    .list-enter-to{
        opacity: 1;
    }*/
    .todo {
        margin: auto;
        background: #fff;
        padding: 20px;
        border-radius: 5px;
        box-shadow: rgba(0, 0, 0, 0.3) 3px 3px 15px;
        width:60%;
        height: 800px;



    .addScroll{
        overflow-y: auto;
    }
    .tabHeight{
        height:500px ;
    }

    .title {
        margin-top: 0;
    }

    .tasks {
        list-style: none;
        padding: 0;
    }

    .complete {
        text-decoration: line-through;
    }

    .input_row {

    .width_input {
        width: 91%;
        display: inline-flex;
    }

    }
    }
</style>
