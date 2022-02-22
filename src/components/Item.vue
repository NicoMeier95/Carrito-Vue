<template>
<tr>
    <th scope="row">{{item.id}}</th>
    <td>{{item.title}}</td>
    <td>{{item.cantidad}}</td>
    <td>
        <button class="btn btn-info btn-sm" @click="aumentar(item.id)">
            +
        </button>
        <button class="btn btn-danger btn-sm" @click="disminuir(item.id)">
            -
        </button>
    </td>
    <td>${{item.precio * item.cantidad}}</td>
</tr> 
</template>

<script>
import {useStore} from 'vuex';

export default {
    props: ['item'],
    setup(){
        const store = useStore();
        const aumentar = id => { store.commit('aumentarCantidad', id ) };
        const disminuir = id => { store.commit('disminuirCantidad', id ) };

        return {aumentar, disminuir}
    }
}
</script>
