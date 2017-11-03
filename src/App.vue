<template>
  <div id="app">
      <h3>{{title}}</h3>
        <div class="form">
            <div class="form-group">
                <div class="form-group">
                    <label>Note Title</label>
                    <input
                        class="form-control"
                        type="text"
                        v-model="note.title">
                </div>
                <div class="form-group">
                    <label>Note text</label>
                    <textarea 
                        class="form-control"
                        v-model="note.text"></textarea>
                </div>
            </div>
            <button 
                class="btn btn-primary"
                @click="addNote">Submit</button>
        </div>
        <div class="col-sm-12">
            <div 
                class="col-sm-4 note"
                v-for="(note, index) in notes"
                v-bind:key="index">
                <div class="card">
                    <button class="close" @click="removeNote(index)">&times;</button>
                    <div class="card-block">
                        <h4 class="card-title">{{note.title}}</h4>
                        <h6 class="card-subtitle mb-2 text-muted">{{note.date}}</h6>
                        <p class="card-text">{{note.text}}</p>
                    </div>
                </div>  
            </div>
        </div>
  </div>
</template>

<script>
    export default {
        name: 'app',
        data() {
            return {
                title: 'Notemaster',
                note: {
                    title: '',
                    text: ''
                },
                notes: [
                    {
                        title: 'Visited Hawaii',
                        text: 'I loved the beaches and delicious fresh coconuts',
                        date: new Date(Date.now()).toLocaleString()
                    }
                ]
            }
        },
        methods: {
            addNote() {
                let { text, title } = this.note
                this.notes.push({
                    text,
                    title,
                    date: new Date(Date.now()).toLocaleDateString()
                })
            },
            removeNote(index) {
                this.note.splice(index, 1)
            }
        }
    }
</script>