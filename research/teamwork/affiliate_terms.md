# Teamwork.com — アフィリエイト規約メモ

調査日: 2026-08-19

## 結論: 継続報酬型（recurring commission）— 確認済み

公式ページ（https://www.teamwork.com/referral-program/）に明記。

## 条件

- **手数料率**: 紹介した顧客が支払うたびに 15%
- **上限**: 1紹介あたり累計 $1,000 まで
- **継続性**: 紹介した顧客が支払いを続ける限り、上限に達するまで継続的に報酬発生（真の意味でのlifetime recurring）
- **紹介人数の上限**: なし
- **参加条件**: Teamwork.comのサイトオーナーであること。紹介者は提供リンク経由・同一ブラウザでサインアップする必要あり
- **支払い**: PayPal、残高$100以上で申請可能

## 公式ソース

- https://www.teamwork.com/referral-program/
- https://support.teamwork.com/projects/subscription/teamwork-referrals

## 次のアクション

- [x] ユーザー自身で https://www.teamwork.com/referral-program/ からアフィリエイト申請
- [x] 承認後、実際のダッシュボード上の最終規約（上記と相違ないか）を再確認

## 実際に確認できたこと（2026-08-19、アカウント作成後）

別途申請フォームは不要だった。**Teamwork.comの無料アカウントを作成した時点で、Settings → More... → Referral にユニークな紹介リンクが自動発行されていた。** 画面表示は「15% commission」と明記されており、上記の規約と一致。Total earnings / Paid / Pendingのダッシュボードも同じ画面で確認可能。

リンクは `.env` の `TEAMWORK_REFERRAL_LINK` に保存する運用とする（gitignore対象なので安全）。
