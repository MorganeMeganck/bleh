

<template>
  <div id="app" class="container">
    
    <section>
        <b-field grouped group-multiline>
            <button class="button field is-danger" @click="checkedRows = []"
                :disabled="!checkedRows.length">
                <b-icon icon="close"></b-icon>
                <span>Clear checked</span>
            </button>
            <b-select v-model="checkboxPosition">
                <option value="left">Checkbox at left</option>
            </b-select>
        </b-field>

        <b-tabs>
            <b-tab-item label="Table">
                <b-table
:data="data"
:columns="columns"
:checked-rows.sync="checkedRows"
:is-row-checkable="(row) => row.id !== 3 && row.id !== 4"
checkable
:checkbox-position="checkboxPosition">

<template slot="header" slot-scope="{ column }">
  <div class="level" style="width:100%;">
    <div>{{ column.label }}</div>
    <b-dropdown onclick="event.stopPropagation()" class="level-right" aria-role="list">
            <button class="button" slot="trigger" slot-scope="{ active }">
                <span><i class="fas fa-filter"></i></span>
                <b-icon :icon="active ? 'menu-up' : 'menu-down'"></b-icon>
            </button>

            <b-dropdown-item aria-role="listitem">Action</b-dropdown-item>
            <b-dropdown-item aria-role="listitem">Another action</b-dropdown-item>
            <b-dropdown-item aria-role="listitem">Something else</b-dropdown-item>
    </b-dropdown>
  </div>
    
</template>
                </b-table>
            </b-tab-item>

            <b-tab-item label="Checked rows">
                <pre>{{ checkedRows }}</pre>
            </b-tab-item>
        </b-tabs>
    </section>

</div>
                
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },

    data() {
        const data = [
            { 'id': 1, 'first_name': 'Jesse', 'last_name': 'Simmons', 'date': '2016-10-15 13:43:27', 'gender': 'Male' },
            { 'id': 2, 'first_name': 'John', 'last_name': 'Jacobs', 'date': '2016-12-15 06:00:53', 'gender': 'Male' },
            { 'id': 3, 'first_name': 'Tina', 'last_name': 'Gilbert', 'date': '2016-04-26 06:26:28', 'gender': 'Female' },
            { 'id': 4, 'first_name': 'Clarence', 'last_name': 'Flores', 'date': '2016-04-10 10:28:46', 'gender': 'Male' },
            { 'id': 5, 'first_name': 'Anne', 'last_name': 'Lee', 'date': '2016-12-06 14:38:38', 'gender': 'Female' }
        ]

        return {
            data,
            checkboxPosition: 'left',
            checkedRows: [data[1], data[3]],
            columns: [
                {
                    field: 'id',
                    label: 'ID',
                    numeric: true,
                    sortable: true,
                },
                {
                    field: 'first_name',
                    label: 'First Name',
                    sortable: true,
                },
                {
                    field: 'last_name',
                    label: 'Last Name',
                },
                {
                    field: 'date',
                    label: 'Date',
                    centered: true
                },
                {
                    field: 'gender',
                    label: 'Gender',
                }
            ]
        }
    }



}

            
        
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
