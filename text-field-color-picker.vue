<template>
    <div>
        <v-text-field placeholder="Votre couleur de fond." rounded outlined v-model="isFontColorSelected" hide-details="" class="ma-0 pl-2">                                             
                    <template v-slot:append>
                        <v-menu  v-model="menu" top nudge-bottom="105" nudge-left="16" :close-on-content-click="false">
                            <template v-slot:activator="\{ on \}">
                                <div :style="switchColor" v-on="on" />
                            </template>
                            <v-card>
                                <v-card-text class="pa-0">
                                    <v-color-picker v-model="isFontColorSelected" flat />
                                </v-card-text>
                            </v-card>
                        </v-menu>
                    </template>
        </v-text-field>
</div>
</template>

<script>

export default {
    data: () => {
        return {
            menu:false,
            isFontColorSelected: '#FBCEB6',
        };
    },
    computed: {
        switchColor() {
            return {
                backgroundColor: this.isFontColorSelected,
                cursor: 'pointer',
                height: '30px',
                width: '30px',
                borderRadius: this.menu ? '50%' : '4px',
                transition: 'border-radius 200ms ease-in-out'

                // Pour Bind la couleur choisie à un élément, utiliser :style="{backgroundColor: isFontColorSelected}"

            };
        },
    },
},

</script>
