<template>
  <cv-feedback-button
    v-if="!hideCopyButton"
    class="cv-code-snippet-inline"
    :class="classes"
    :disabled="disabled"
    :feedback="copyFeedback"
    inline
    :title="feedbackAriaLabel"
    :ariaLabel="feedbackAriaLabel"
    @click="$emit('copy-code')"
    ><slot
  /></cv-feedback-button>
  <span v-else :class="classes"><slot /></span>
</template>

<script>
import CvFeedbackButton from '../cv-feedback-button/_cv-feedback-button';
import { carbonPrefixMixin } from '../../mixins';

export default {
  name: 'CvCodeSnippetInline',
  mixins: [carbonPrefixMixin],
  components: {
    CvFeedbackButton,
  },
  props: {
    copyFeedback: String,
    disabled: Boolean,
    feedbackAriaLabel: String,
    hideCopyButton: Boolean,
  },
  computed: {
    classes() {
      return [`${this.carbonPrefix}--snippet`, `${this.carbonPrefix}--snippet--inline`];
    },
  },
};
</script>
