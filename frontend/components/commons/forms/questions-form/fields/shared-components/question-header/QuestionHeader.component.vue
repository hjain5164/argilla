<template>
  <div class="title-area --body1">
    <span v-text="title" v-optional-field="!isRequired" />

    <BaseIconWithBadge
      class="icon-info"
      v-if="showIcon"
      icon="info"
      :id="`${title}QuestionHeader`"
      :show-badge="false"
      iconColor="#acacac"
      badge-vertical-position="top"
      badge-horizontal-position="right"
      badge-border-color="white"
      v-tooltip="{ content: tooltipMessage, backgroundColor: '#FFF' }"
    />
  </div>
</template>

<script>
export default {
  name: "QuestionHeader",
  props: {
    title: {
      type: String,
      required: true,
    },
    tooltipMessage: {
      type: String,
      default: () => "",
    },
    isRequired: {
      type: Boolean,
      default: () => false,
    },
  },
  computed: {
    showIcon() {
      // TODO - move this to the template to after reviewing the jest.config
      return this.tooltipMessage?.length ? true : false;
    },
  },
};
</script>

<style lang="scss" scoped>
.title-area {
  color: $black-87;
  font-weight: 500;
}

.icon {
  color: $black-37;
}

.info-icon {
  display: flex;
  flex-basis: 37px;
}

span {
  word-break: break-word;
}

.icon-info {
  display: inline-flex;
  width: 20px;
  height: 20px;
  margin: 0;
  padding: 0;
  overflow: inherit;
  vertical-align: middle;
  &[data-title] {
    position: relative;
    overflow: visible;
    &:before,
    &:after {
      margin-top: 0;
    }
  }
}
</style>
