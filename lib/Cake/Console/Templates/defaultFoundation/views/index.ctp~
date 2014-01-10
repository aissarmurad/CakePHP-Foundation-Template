<?php
/**
 *
 * Aissar Murad - http://facebook.com/aissarmurad - aissarmurad at gmail dot com
 * 
 * Licensed under The MIT License
 * For full copyright and license information, please see the LICENSE.txt
 * Redistributions of files must retain the above copyright notice.
 *
 * @copyright     It has no copyright. But I would like to earn a few energy drinks. :D
 * @link          aissarmurad at gmail dot com
 * @package       Cake.Console.Templates.defaultFoundation.views
 * @since         CakePHP(tm) v 2.4.x
 * @license       http://www.opensource.org/licenses/mit-license.php MIT License
 */
?>
<div class="row">
<div class="actions button-bar">
	<h3><?php echo "<?php echo __('Actions'); ?>"; ?></h3>
        <ul class="button-group">
            <li class="button tiny radius"><?php echo "<?php echo \$this->Html->link(__('New " . $singularHumanName . "'), array('action' => 'add')); ?>"; ?></li>
<?php
	$done = array();
	foreach ($associations as $type => $data) {
		foreach ($data as $alias => $details) {
			if ($details['controller'] != $this->name && !in_array($details['controller'], $done)) {
				echo "\t\t<li class='button tiny radius'><?php echo \$this->Html->link(__('List " . Inflector::humanize($details['controller']) . "'), array('controller' => '{$details['controller']}', 'action' => 'index')); ?> </li>\n";
				echo "\t\t<li class='button tiny radius'><?php echo \$this->Html->link(__('New " . Inflector::humanize(Inflector::underscore($alias)) . "'), array('controller' => '{$details['controller']}', 'action' => 'add')); ?> </li>\n";
				$done[] = $details['controller'];
			}
		}
	}
?>
	</ul>
</div>
</div>
<div class="row">
<div class="<?php echo $pluralVar; ?> index small-12 small-centered">
	<h2><?php echo "<?php echo __('{$pluralHumanName}'); ?>"; ?></h2>
        <table cellpadding="0" cellspacing="0" class="responsive">
	<tr>
	<?php foreach ($fields as $field): ?>
                    <?php if(!empty($field)){ ?>
                    <?php preg_replace("/([a-zA-Z0-9]+)(_id)/x", "$1", $field);?>
                    <th><?php echo "<?php echo \$this->Paginator->sort('{$field}'); ?>"; } ?></th>
	<?php endforeach; ?>
		<th class="actions"><?php echo "<?php echo __('Actions'); ?>"; ?></th>
	</tr>
	<?php
	echo "<?php foreach (\${$pluralVar} as \${$singularVar}): ?>\n";
	echo "\t<tr>\n";
		foreach ($fields as $field) {
			$isKey = false;
			
                        if (!empty($associations['belongsTo']) /*or !empty($associations['hasOne'])*/) {
				foreach (/*(!empty($associations['belongsTo']))?*/ $associations['belongsTo'] /*: $associations['hasOne']*/ as $alias => $details) {
                                    /*preg_match("/([a-zA-Z0-9]+)(_id)/x", $field, $output_array);*/
                                    /*$matchREGEX = !empty($output_array[0]);*/   /* SOMEONE, PLEASE FIX IT TO ME */
                                    /*$isLikeID = ($field=='id')? true : false;*/
					if ($field === $details['foreignKey'] /*and !$isLikeID or $matchREGEX*/) {
						$isKey = true;
						echo "\t\t<td>\n\t\t\t<?php echo \$this->Html->link(\${$singularVar}['{$alias}']['{$details['displayField']}'], array('controller' => '{$details['controller']}', 'action' => 'view', \${$singularVar}['{$alias}']['{$details['primaryKey']}'])); ?>\n\t\t</td>\n";
						break;
					}
				}
			}
                        
			if ($isKey !== true) {
				echo "\t\t<td><?php echo h(\${$singularVar}['{$modelClass}']['{$field}']); ?>&nbsp;</td>\n";
			}
		}

		echo "\t\t<td class=\"actions\">\n";
		echo "\t\t\t<?php echo \$this->Html->link(__('View'), array('action' => 'view', \${$singularVar}['{$modelClass}']['{$primaryKey}'])); ?>\n";
		echo "\t\t\t<?php echo \$this->Html->link(__('Edit'), array('action' => 'edit', \${$singularVar}['{$modelClass}']['{$primaryKey}'])); ?>\n";
		echo "\t\t\t<?php echo \$this->Form->postLink(__('Delete'), array('action' => 'delete', \${$singularVar}['{$modelClass}']['{$primaryKey}']), null, __('Are you sure you want to delete # %s?', \${$singularVar}['{$modelClass}']['{$primaryKey}'])); ?>\n";
		echo "\t\t</td>\n";
	echo "\t</tr>\n";

	echo "<?php endforeach; ?>\n";
	?>
	</table>
        <p class="text-center">
	<?php echo "<?php
	echo \$this->Paginator->counter(array(
	'format' => __('Page {:page} of {:pages}, showing {:current} records out of {:count} total, starting on record {:start}, ending on {:end}')
	));
	?>"; ?>
	</p>
        <div class="pagination-centered">
	<ul class="paging pagination text-center">
	<?php
                echo "<?php\n";
		echo "\t\techo \$this->Paginator->prev('< ' . __('previous'), array('tag' => 'li', 'currentClass' => 'current', 'first' => 1, 'last' => 1), null, array('tag' => 'li','class' => 'prev arrow unavailable','disabledTag' => 'a'));\n";
		echo "\t\techo \$this->Paginator->numbers(array('separator' => '','currentTag' => 'a', 'currentClass' => 'current','tag' => 'li','first' => 1, 'last' => 1));\n";
		echo "\t\techo \$this->Paginator->next(__('next') . ' >', array('tag' => 'li', 'currentClass' => 'current', 'first' => 1, 'last' => 1), null, array('tag' => 'li','class' => 'next arrow unavailable','disabledTag' => 'a'));\n";
		echo "\t?>\n";
	?>
	</ul>
        </div>
</div>
</div>