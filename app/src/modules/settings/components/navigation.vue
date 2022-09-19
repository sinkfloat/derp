<template>
	<v-list nav>
		<v-list-item v-for="item in navItems" :key="item.to" :to="item.to">
			<v-list-item-icon><v-icon :name="item.icon" /></v-list-item-icon>
			<v-list-item-content>
				<v-text-overflow :text="item.name" />
			</v-list-item-content>
		</v-list-item>	
	</v-list>
</template>

<script lang="ts">
import { useI18n } from 'vue-i18n';
import { defineComponent, computed } from 'vue';
import { version } from '../../../../package.json';

export default defineComponent({
	setup() {
		const { t } = useI18n();

		const navItems = [
			{
				icon: 'public',
				name: t('settings_project'),
				to: `/settings/project`,
			},
			{
				icon: 'list_alt',
				name: t('settings_data_model'),
				to: `/settings/data-model`,
			},
			{
				icon: 'admin_panel_settings',
				name: t('settings_permissions'),
				to: `/settings/roles`,
			},
			{
				icon: 'bookmark_border',
				name: t('settings_presets'),
				to: `/settings/presets`,
			},
			{
				icon: 'translate',
				name: t('settings_translation_strings'),
				to: `/settings/translation-strings`,
			},
			{
				icon: 'anchor',
				name: t('settings_webhooks'),
				to: `/settings/webhooks`,
			},
			{
				icon: 'bolt',
				name: t('settings_flows'),
				to: `/settings/flows`,
			},
		];

		return { version, navItems };
	},
});
</script>

<style scoped>
.version .v-icon {
	color: var(--foreground-subdued);
	transition: color var(--fast) var(--transition);
}

.version :deep(.v-text-overflow) {
	color: var(--foreground-subdued);
	transition: color var(--fast) var(--transition);
}

.version:hover .v-icon {
	color: var(--foreground-normal-alt);
}

.version:hover :deep(.v-text-overflow) {
	color: var(--foreground-normal-alt);
}
</style>
