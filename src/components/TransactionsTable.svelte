<script lang="ts">
  import { wallet } from '../stores/wallet';
  import { transactions } from '../stores/transactions';
  import { baseWebURL } from '../application/explorer';

  const makeLink = (hash: string) => {
    const baseURL = baseWebURL($wallet.network) + '/tx';
    return `${baseURL}/${hash}`;
  };
</script>

<table class="table">
  <thead>
    <tr>
      <th>Index</th>
      <th>Hash</th>
      <th>Explorer</th>
    </tr>
  </thead>
  <tbody>
    {#each $transactions as transaction, index}
      <tr>
        <td>{index}</td>
        <td>{transaction.txID}</td>
        <td>
          <a target="_blank" href={makeLink(transaction.txID)}>
            <span class="icon">
              <i class="fas fa-link" />
            </span>
          </a>
        </td>
      </tr>
    {/each}
  </tbody>
</table>

<style src="./scss/main.scss" lang="scss" global></style>
