<script setup lang="ts">
const columns = [{
  label: 'Recursos',
  children: [{
    label: 'Central de Ajuda'
  }, {
    label: 'Documentação'
  }, {
    label: 'Roteiro'
  }, {
    label: 'Registro de Mudanças'
  }]
}, {
  label: 'Funcionalidades',
  children: [{
    label: 'Afiliados'
  }, {
    label: 'Portal'
  }, {
    label: 'Vagas'
  }, {
    label: 'Patrocinadores'
  }]
}, {
  label: 'Empresa',
  children: [{
    label: 'Sobre'
  }, {
    label: 'Preços'
  }, {
    label: 'Carreiras'
  }, {
    label: 'Blog'
  }]
}]

const toast = useToast()

const email = ref('')
const loading = ref(false)

function onSubmit() {
  loading.value = true

  toast.add({
    title: 'Inscrito!',
    description: 'Você foi inscrito em nossa newsletter.'
  })
}
</script>

<template>
  <USeparator
    icon="i-simple-icons-nuxtdotjs"
    class="h-px"
  />

  <UFooter :ui="{ top: 'border-b border-default' }">
    <template #top>
      <UContainer>
        <UFooterColumns :columns="columns">
          <template #right>
            <form @submit.prevent="onSubmit">
              <UFormField
                name="email"
                label="Inscreva-se em nossa newsletter"
                size="lg"
              >
                <UInput
                  v-model="email"
                  type="email"
                  class="w-full"
                  placeholder="Digite seu e-mail"
                >
                  <template #trailing>
                    <UButton
                      type="submit"
                      size="xs"
                      label="Inscrever"
                    />
                  </template>
                </UInput>
              </UFormField>
            </form>
          </template>
        </UFooterColumns>
      </UContainer>
    </template>

    <template #left>
      <p class="text-sm text-muted">
        Construído com Nuxt UI • © {{ new Date().getFullYear() }}
      </p>
    </template>

    <template #right>
      <UButton
        to="https://go.nuxt.com/discord"
        target="_blank"
        icon="i-simple-icons-discord"
        aria-label="Nuxt no Discord"
        color="neutral"
        variant="ghost"
      />
      <UButton
        to="https://go.nuxt.com/x"
        target="_blank"
        icon="i-simple-icons-x"
        aria-label="Nuxt no X"
        color="neutral"
        variant="ghost"
      />
      <UButton
        to="https://github.com/nuxt-ui-templates/landing"
        target="_blank"
        icon="i-simple-icons-github"
        aria-label="Nuxt UI no GitHub"
        color="neutral"
        variant="ghost"
      />
    </template>
  </UFooter>
</template>
