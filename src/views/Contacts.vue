<template>
    <div class="contacts">
        <dx-data-grid
                :columns="columns"
                :show-borders="true"
                :data-source="dataSource"
                key-expr="ID">
            <dx-filter-row
                    :visible="showFilterRow"
                              />
            <dx-header-filter
                    :visible="showHeaderFilter"
            />
            <dx-group-panel :visible="true"/>
            <dx-grouping :auto-expand-all="autoExpandAll"/>
            <dx-paging :page-size="35"/>
            <dx-search-panel :visible="true" placeholder="Search..."/>
            <dx-editing
                    :allow-updating="true"
                    mode="popup"
            >

                <dx-popup
                        :show-title="true"
                        :width="700"
                        :height="230"
                        title="Информация о сотруднике"
                >
                    <dx-position
                            my="top"
                            at="top"
                            of="window"
                    />
                </dx-popup>
            </dx-editing>

            <dx-column
                    :width="80"
                    data-field="tn"


            />
            <dx-column
                    :width="115"
                    data-field="bw"
                    data-type="date"
            />
            <dx-column
                    :width="115"
                    data-field="ew"
                    data-type="date"

            />
            <dx-summary>
                <dx-total-item
                        column="fio"
                        summary-type="count"
                />
                <!--<dx-total-item-->
                        <!--:customize-text="customizeDate"-->
                        <!--column="OrderDate"-->
                        <!--summary-type="min"-->
                <!--/>-->
                <!--<dx-total-item-->
                        <!--column="SaleAmount"-->
                        <!--summary-type="sum"-->
                        <!--value-format="currency"-->
                <!--/>-->
                <dx-group-item
                        :show-in-group-footer="true"
                        column="fio"
                        summary-type="count"
                        display-format="Всего: {0}"
                />
            </dx-summary>
            <dx-sort-by-group-summary-info summary-item="count"/>
        </dx-data-grid>
        <dx-button :text='text' v-on:click="showmessgae"/>
        <dx-text-box v-model="textEdit"/>
        <dx-check-box
                :value.sync="autoExpandAll"
                text="Expand All Groups"/>
    </div>
</template>
<script>
    import 'devextreme/dist/css/dx.common.css';
    // import 'devextreme/dist/css/dx.material.blue.dark.css';
    import 'devextreme/dist/css/dx.darkmoon.compact.css';
    import DxButton from 'devextreme-vue/button';
    import DxTextBox from 'devextreme-vue/text-box';
    import DxCheckBox from 'devextreme-vue/check-box';
    import {
        DxDataGrid,
        DxColumn,
        DxEditing,
        DxGroupPanel,
        DxGrouping,
        DxPopup,
        DxPosition,
        DxSearchPanel,
        DxPaging,
        DxSummary,
        DxTotalItem,
        DxGroupItem,
        DxSortByGroupSummaryInfo,
        DxHeaderFilter,
        DxFilterRow
    } from 'devextreme-vue/data-grid';
    import {users} from '../data/users.js';

    export default {
        name: 'HelloWorld',
        data() {
            return {
                text: 'Hello!',
                textEdit: 'Yo world',
                dataSource: users,
                columns: ['fio', 'dep', 'prof'],
                autoExpandAll: false,
                showFilterRow: true,
                showHeaderFilter: true,
                              dataGridRefName: 'dataGrid'
            };
        },
        methods: {
            showmessgae() {
                alert(this.textEdit)
                //this.setSort()
            }
        },
        components: {
            DxDataGrid,
            DxButton,
            DxTextBox,
            DxColumn,
            DxPopup,
            DxEditing,
            DxPosition,
            DxSearchPanel,
            DxGroupPanel,
            DxGrouping,
            DxCheckBox,
            DxPaging,
            DxSummary,
            DxTotalItem,
            DxGroupItem,
            DxSortByGroupSummaryInfo,
            DxHeaderFilter,
            DxFilterRow
        }
    };
</script>

<style scoped>
    .options {
        padding: 20px;
        margin-top: 20px;
        background-color: rgba(191, 191, 191, 0.15);
    }

    .caption {
        font-size: 18px;
        font-weight: 500;
    }

    .option {
        margin-top: 10px;
    }
</style>