<template>
    <v-container class="filter">
        <v-flex v-if="!collapse" class="px-0">
          <SearchOptionExpandButton
            :handleClick="handleExpand"
            :selectedOption="currentFilter.optionName"
          />
          <SearchOptionMenu
            :visibility="currentFilter.datePickerVisible"
            :selectedDate="selectedDate"
          />
        </v-flex>
        <v-card class="pl-3 pr-4 filter--list" v-if="collapse">
            <SearchOptionHeader
              :handleClose="handleClose"
            />
            <v-divider dark></v-divider>
            <SearchOptionRow
              :data="['Last 24 hours', 'Exact date', 'Date Range']"
              :setOption="setOption"
            />
            <v-divider dark></v-divider>
            <SearchOptionRow
              :data="['Last week', 'Exact 2 week']"
              :setOption="setOption"
            />
            <v-divider dark></v-divider>
            <SearchOptionRow
              :data="['Last month', 'Last 2 months', 'Last 3 months', 'Last 6 months']"
              :setOption="setOption"
            />
            <v-divider dark></v-divider>
            <SearchOptionRow
              :data="['Last year', 'Last 2 years']"
              :setOption="setOption"
            />
        </v-card>
    </v-container>
</template>
<script>
import { mapGetters } from 'vuex';
import SearchOptionExpandButton from '../atoms/SearchOptionExpandButton';
import SearchOptionMenu from '../atoms/SearchOptionMenu';
import SearchOptionHeader from '../atoms/SearchOptionHeader';
import SearchOptionRow from '../atoms/SearchOptionRow';

export default {
  components: {
    SearchOptionExpandButton,
    SearchOptionMenu,
    SearchOptionHeader,
    SearchOptionRow,
  },
  data() {
    return {
      collapse: false,
      selectedDate: null,
    };
  },
  methods: {
    setOption(optionValue) {
      if (optionValue === 'Exact date') {
        this.$store.dispatch('setFilter', { optionName: optionValue, datePickerVisible: true, selectedDate: this.selectedDate });
      } else {
        this.$store.dispatch('setFilter', { optionName: optionValue, datePickerVisible: false });
      }
      this.collapse = false;
    },
    handleExpand() {
      this.collapse = true;
    },
    handleClose() {
      this.collapse = false;
    },
  },
  watch: {
    selectedDate(newValue) {
      this.$store.dispatch('setDate', newValue);
    },
  },
  computed: {
    ...mapGetters({
      currentFilter: 'currentState',
    }),
  },
};
</script>
<style scoped lang="less">
@import '../../assets/styles/theme.less';
.filter {
  .btn.btn--selector{
    background-color: @background-grey;
    color: @selector-color;
    font-weight: 600;
    height: auto;
  }
}

.filter--list {
  background-color: @background-grey;
}
</style>
