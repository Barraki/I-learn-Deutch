<template>

	<v-app>
		<v-navigation-drawer absolute temporary v-model="drawer" class="hidden-md-and-up">
			<v-list>
				<v-list-tile v-for="(item, i) in menuItems" v-bind:key="`navdrawer$(i)`">
					<v-list-tile-action>
						<v-icon v-html="item.icon"></v-icon>
					</v-list-tile-action>
					<v-list-tile-content>
						<v-list-title v-text="item.title"></v-list-title>
					</v-list-tile-content>
				</v-list-tile>
			</v-list>
		</v-navigation-drawer>
		<v-toolbar app dark class="primary" >
			<v-toolbar-side-icon @click.stop="drawer =! drawer" class="hidden-md-and-up"></v-toolbar-side-icon> 
			<v-toolbar-title v-text="'Ich Lerne Deutch'"></v-toolbar-title>
			<v-spacer></v-spacer>
			<v-toolbar-items class="hidden-sm-and-down">
				<v-btn v-for="(item, i) in menuItems" flat v-bind:key="`menuitem$(i)`" v-bind:to="item.route">
					<v-icon left v-html="item.icon"> {{ item.icon }} </v-icon>{{ item.title }}
				</v-btn>
			</v-toolbar-items>
		</v-toolbar>
	</v-app>

</template>

<script>
	// @ is an alias to /src

	export default {
					data() {
				return {
					drawer: false
				}
			},
		computed: {

			menuItems() {
				return [{
						icon: 'visibility',
						title: 'Читать',
						route: '/books',
					},
					{
						icon: 'extension',
						title: 'Учить слвоа',
						route: '/words',
					},
					{
						icon: 'account_circle',
						title: 'Мой кабинет',
						route: '/profile',
					},
					{
						icon: 'exit_to_app',
						title: 'Выйти',
						route: '/logout',
					},
					{
						icon: 'input',
						title: 'Войти',
						route: '/signin',
					},
					{
						icon: 'lock_open',
						title: 'Зарегистрироваться',
						route: '/signup',
					},
				]
			}
		}
	}
</script>