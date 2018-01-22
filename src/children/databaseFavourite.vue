<template>
    <div id="databaseFavourite">
        <el-table @cell-click="favouriteDetail" :data="tableFavouriteData" border style="width: 100%"
                  empty-text="Nothing">
            <el-table-column prop="date" label="Name" className="column1" width="430"></el-table-column>
            <el-table-column width="170" label="Update Notification">
                <template slot-scope="updateScope">
                    <el-switch @change="updateControl($event,updateScope.row.id)" v-model="updateScope.row.switchValue"
                               active-color="#13ce66" inactive-color="#ff4949"></el-switch>
                </template>
            </el-table-column>
            <el-table-column prop="name" label="Update Info" width="160"></el-table-column>
            <el-table-column label="Delete" className="abFavouriteDelete">
                <template slot-scope="deleteScope">
                    <el-button class="el-icon-close" type="text" @click="dialogVisible = true"></el-button>
                    <el-dialog title="提示" :visible.sync="dialogVisible" width="30%">
                        <span>这是一段信息</span>
                        <span slot="footer" class="dialog-footer">
                            <el-button @click="dialogVisible = false">取 消</el-button>
                            <el-button type="primary" @click="deleteRow(deleteScope.row.id)">确 定</el-button>
                        </span>
                    </el-dialog>
                </template>
            </el-table-column>
        </el-table>
    </div>
</template>
<script>
    export default {
        name: 'databaseFavourite',
        data() {
            return {
                dialogVisible: false,
                tableFavouriteData: [
                    {
                        date: '1China November 2017 Non-Compliant Imported Food Data..',
                        name: '2018-3-1',
                        address: 'To be enforced',
                        id: 1,
                        switchValue: true
                    }, {
                        date: '2China November 2017 Non-Compliant Imported Food Data..',
                        name: '2018-3-1',
                        address: 'To be enforced',
                        id: 2,
                        switchValue: false
                    }, {
                        date: '3China November 2017 Non-Compliant Imported Food Data..',
                        name: '2018-3-1',
                        address: 'To be enforced',
                        id: 3,
                        switchValue: true
                    }, {
                        date: '4China November 2017 Non-Compliant Imported Food Data..',
                        name: '2018-3-1',
                        address: 'To be enforced',
                        id: 4,
                        switchValue: false
                    }, {
                        date: '5China November 2017 Non-Compliant Imported Food Data..',
                        name: '2018-3-1',
                        address: 'To be enforced',
                        id: 5,
                        switchValue: true
                    }
                ],

            }
        },
        methods: {
            favouriteDetail: function (row, column, cell, event) {
                if (column.className === 'column1') {
                    console.log(row.id)
                }
            },
            updateControl: function (status, id) {
                console.log(status, id)
            },
            deleteRow: function (data) {
                console.log(data)
                let newTableFavouriteData = [];
                for (let i = 0; i < this.tableFavouriteData.length; i++) {
                    if (this.tableFavouriteData[i].id !== data) {
                        newTableFavouriteData.push(this.tableFavouriteData[i])
                    }
                }
                // this.tableFavouriteData = newTableFavouriteData;
                // this.dialogVisible = false
            },

        }
    }
</script>
<style lang="scss">
    #databaseFavourite {
        $borderColor: #c5a835;
        $textColor: #5a5050;
        .el-table {
            font-size: 13px;
            .column1 {
                color: #5959b9;
                cursor: pointer;
                &:hover {
                    text-decoration: underline;
                }
            }
            .el-button {
                padding: 3px 10px;
            }

            tr:hover > td {
                background-color: white;
            }
            border-color: $borderColor;
            &::before {
                background-color: $borderColor;
            }
            &::after {
                background-color: $borderColor;
            }
            th {
                background-color: #f0e4d6;
                text-align: center;
                border-right: none;
                border-color: $borderColor;
                padding: 5px 0;
                color: $textColor !important;
            }
            td {
                text-align: center;
                border-right: none;
                border-color: $borderColor;
                padding: 5px 0;
            }
        }
        .el-pagination {
            margin: 30px auto;
        }
        .abFavouriteDelete {
            .el-icon-close {
                font-size: 17px;
                font-weight: 600;
                color: #605b6b;
                cursor: pointer;
                &:hover {
                    color: #f00e45;
                }
            }
        }
    }
</style>


