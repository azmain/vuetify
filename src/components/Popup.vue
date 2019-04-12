<template>
    <div class="popup">
        <v-dialog max-width="600px" v-model="dialog">
            <v-btn flat slot="activator" class="success">
                Add new project
            </v-btn>

            <v-card>
                <v-card-title>
                    <h2>New Project</h2>
                </v-card-title>
                <v-card-text>
                    <v-form ref="form">
                        <v-text-field 
                            label="Title" 
                            v-model="title"
                            prepend-icon="folder"
                            :rules="inputValidations">
                        </v-text-field>
                        <v-textarea 
                            label="Information" 
                            v-model="content"
                            prepend-icon="edit"
                            :rules="inputValidations">
                        </v-textarea>

                        <!-- Datepicker -->
                        <v-menu>
                            <v-text-field 
                                slot="activator" 
                                label="Due Date" 
                                :value="formattedDate"
                                prepend-icon="date_range"
                                :rules="inputValidations">
                            </v-text-field>

                            <v-date-picker v-model="due">

                            </v-date-picker>
                        </v-menu>

                        <v-spacer></v-spacer>

                        <v-btn flat class="success mx-0 mt-3" :loading="loading" @click="submit">
                            Add Project
                        </v-btn>
                    </v-form>
                </v-card-text>
            </v-card>
        </v-dialog>
    </div>
</template>

<script>
import format from 'date-fns/format'
export default {
    name: "Popup",
    data(){
        return {
            title: '',
            content: '',
            due: '',
            inputValidations: [
                v => v.length >= 3 || "Minimum length is 3."
            ],
            loading: false,
            dialog: false,
        }
    },
    methods: {
        submit(){
            if(this.$refs.form.validate()){
                this.loading = true;
                console.log(this.title, this.content);
                this.loading = false;
                this.dialog = false;
                this.$emit('projectAdded');
            }
        }
    },
    computed:{
        formattedDate(){
            return this.due ? format(this.due, 'Do MMM YYYY') : '';
        }
    }
}
</script>
