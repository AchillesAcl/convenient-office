<template>
  <div>
    <el-row>
      <el-col>
        <div class="box-card">
          <el-row :gutter="20">
            <el-col :span="8">
              <el-card shadow="hover" header="222">
                <div slot="header" class="clearfix">
                  <svg-icon icon-class="international" />
                  <span style="margin-left:10px;">工作相关</span>
                </div>
                <div>
             <span><a href="#">1</a></span><span><a href="#">warnin</a></span>
                </div>
              </el-card>
            </el-col>
            <el-col :span="8">
              <el-card shadow="hover">
                <div slot="header" class="clearfix">
                  <svg-icon icon-class="international" />
                  <span style="margin-left:10px;">{{ $t('i18nView.title') }}</span>
                </div>鼠标悬浮时显示
              </el-card>
            </el-col>
            <el-col :span="8">
              <el-card shadow="hover">
                <div slot="header" class="clearfix">
                  <svg-icon icon-class="international" />
                  <span style="margin-left:10px;">{{ $t('i18nView.title') }}</span>
                </div>从不显示
              </el-card>
            </el-col>
          </el-row>
        </div>
      </el-col>
      <el-col>
        <div class="box-card">
          <el-row :gutter="20">
            <el-col :span="8">
              <el-card shadow="hover">
                <div slot="header" class="clearfix">
                  <svg-icon icon-class="international" />
                  <span style="margin-left:10px;">{{ $t('i18nView.title') }}</span>
                </div>总是显示
              </el-card>
            </el-col>
            <el-col :span="8">
              <el-card shadow="hover">
                <div slot="header" class="clearfix">
                  <svg-icon icon-class="international" />
                  <span style="margin-left:10px;">{{ $t('i18nView.title') }}</span>
                </div>鼠标悬浮时显示
              </el-card>
            </el-col>
            <el-col :span="8">
              <el-card shadow="hover">
                <div slot="header" class="clearfix">
                  <svg-icon icon-class="international" />
                  <span style="margin-left:10px;">{{ $t('i18nView.title') }}</span>
                </div>从不显示
              </el-card>
            </el-col>
          </el-row>
        </div>
      </el-col>
    </el-row>
    <el-row :gutter="20" style="margin:100px 15px 50px;">
      <el-col :span="12" :xs="24">
        <div class="block">
          <el-date-picker v-model="date" :placeholder="$t('i18nView.datePlaceholder')" type="date" />
        </div>
        <div class="block">
          <el-select v-model="value" :placeholder="$t('i18nView.selectPlaceholder')">
            <el-option v-for="item in options" :key="item.value" :label="item.label" :value="item.value" />
          </el-select>
        </div>
        <div class="block">
          <el-button class="item-btn" size="small">{{ $t('i18nView.default') }}</el-button>
          <el-button class="item-btn" size="small" type="primary">{{ $t('i18nView.primary') }}</el-button>
          <el-button class="item-btn" size="small" type="success">{{ $t('i18nView.success') }}</el-button>
          <el-button class="item-btn" size="small" type="info">{{ $t('i18nView.info') }}</el-button>
          <el-button class="item-btn" size="small" type="warning">{{ $t('i18nView.warning') }}</el-button>
          <el-button class="item-btn" size="small" type="danger">{{ $t('i18nView.danger') }}</el-button>
        </div>
      </el-col>
      <el-col :span="12" :xs="24">
        <el-table :data="tableData" fit highlight-current-row border="" style="width: 100%">
          <el-table-column :label="$t('i18nView.tableName')" prop="name" width="100" align="center" />
          <el-table-column :label="$t('i18nView.tableDate')" prop="date" width="120" align="center" />
          <el-table-column :label="$t('i18nView.tableAddress')" prop="address" />
        </el-table>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import local from "./local";
const viewName = "i18nView";

export default {
  name: "I18n",
  data() {
    return {
      date: "",
      tableData: [
        {
          date: "2016-05-03",
          name: "Tom",
          address: "No. 189, Grove St, Los Angeles"
        },
        {
          date: "2016-05-02",
          name: "Tom",
          address: "No. 189, Grove St, Los Angeles"
        },
        {
          date: "2016-05-04",
          name: "Tom",
          address: "No. 189, Grove St, Los Angeles"
        },
        {
          date: "2016-05-01",
          name: "Tom",
          address: "No. 189, Grove St, Los Angeles"
        }
      ],
      options: [],
      value: ""
    };
  },
  computed: {
    lang: {
      get() {
        return this.$store.state.app.language;
      },
      set(lang) {
        this.$i18n.locale = lang;
        this.$store.dispatch("setLanguage", lang);
      }
    }
  },
  watch: {
    lang() {
      this.setOptions();
    }
  },
  created() {
    if (!this.$i18n.getLocaleMessage("en")[viewName]) {
      this.$i18n.mergeLocaleMessage("en", local.en);
      this.$i18n.mergeLocaleMessage("zh", local.zh);
    }
    this.setOptions(); // set default select options
  },
  methods: {
    setOptions() {
      this.options = [
        {
          value: "1",
          label: this.$t("i18nView.one")
        },
        {
          value: "2",
          label: this.$t("i18nView.two")
        },
        {
          value: "3",
          label: this.$t("i18nView.three")
        }
      ];
    }
  }
};
</script>

<style scoped>
.box-card {
  width: 1600px;
  max-width: 100%;
  margin: 20px auto;
}
.item-btn {
  margin-bottom: 15px;
  margin-left: 0px;
}
.block {
  padding: 25px;
}
</style>
