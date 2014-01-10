<?php
/**
 *
 * Aissar Murad - aissarmurad at gmail dot com
 * 
 * Licensed under The MIT License
 * For full copyright and license information, please see the LICENSE.txt
 * Redistributions of files must retain the above copyright notice.
 *
 * @copyright     It has no copyright. But I would like to earn a few energy drinks. :D
 * @link          aissarmurad at gmail dot com
 * @package       Cake.Console.Templates.default.views
 * @since         CakePHP(tm) v 2.4.x
 * @license       http://www.opensource.org/licenses/mit-license.php MIT License
 */
?>

<div class="row">
<div class="actions button-bar">
	<h3><?php echo "<?php echo __('Actions'); ?>"; ?></h3>
        <ul class="button-group">

<?php if (strpos($action, 'add') === false): ?>
                <li class="button tiny radius"><?php echo "<?php echo \$this->Form->postLink(__('Delete'), array('action' => 'delete', \$this->Form->value('{$modelClass}.{$primaryKey}')), null, __('Are you sure you want to delete # %s?', \$this->Form->value('{$modelClass}.{$primaryKey}'))); ?>"; ?></li>
<?php endif; ?>
                <li class="button tiny radius"><?php echo "<?php echo \$this->Html->link(__('List " . $pluralHumanName . "'), array('action' => 'index')); ?>"; ?></li>
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
<div class="<?php echo $pluralVar; ?> form small-12 small-centered">
<?php echo "<?php echo \$this->Form->create('{$modelClass}'); ?>\n"; ?>
	<fieldset>
		<legend><?php printf("<?php echo __('%s %s'); ?>", Inflector::humanize($action), $singularHumanName); ?></legend>
<?php
		echo "\t<?php\n";
		foreach ($fields as $field) {
			if (strpos($action, 'add') !== false && $field == $primaryKey) {
				continue;
			} elseif (!in_array($field, array('created', 'modified', 'updated'))) {
				echo "\t\techo \$this->Form->input('{$field}');\n";
			}
		}
		if (!empty($associations['hasAndBelongsToMany'])) {
			foreach ($associations['hasAndBelongsToMany'] as $assocName => $assocData) {
				echo "\t\techo \$this->Form->input('{$assocName}');\n";
			}
		}
		echo "\t?>\n";
?>
	</fieldset>
<?php
        echo "<?php echo \$this->Form->button(__('Reset',true), array('type'=>'reset','class'=>'button alert left')); ?>\n";
        echo "<?php echo \$this->Form->submit(__('Submit',true), array('class'=>'button large success right')); ?>\n";
        echo "<?php echo \$this->Form->end(); ?>\n";
?>
</div>
</div>