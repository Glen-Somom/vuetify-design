<template>
  <v-container>
    <v-row justify="center" align="center">
      <v-col cols="6">
        <p v-for="a in 20" :key="a">
          Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's
          standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make
          a
          type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting,
          remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing
          Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions
          of
          Lorem Ipsum.
        </p>
      </v-col>
      <ExpandableButton />
    </v-row>
  </v-container>
</template>

<script>
import ExpandableButton from "@/components/ActionsOverlay";

export default {
  components: {ExpandableButton},
  setup() {
    const actions = [
      {title: "Cancel"},
      {title: "Email"},
      {title: "Download"},
    ];
    return {actions};
  }
}
</script>
